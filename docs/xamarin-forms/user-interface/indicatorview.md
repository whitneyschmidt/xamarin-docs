---
title: "Xamarin.Forms IndicatorView"
description: "The IndicatorView is a control that displays indicators that represent the number of items, and current position, in a CarouselView."
ms.prod: xamarin
ms.assetId: BBCC223B-4B02-46B7-80BB-EE0E86A67CE2
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 12/11/2019
---

# Xamarin.Forms IndicatorView

![](~/media/shared/preview.png "This API is currently pre-release")

[![Download Sample](~/media/shared/download.png) Download the sample](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-indicatorviewdemos/)

The `IndicatorView` is a control that displays indicators that represent the number of items, and current position, in a `CarouselView`:

[![Screenshot of a CarouselView and IndicatorView, on iOS and Android](indicatorview-images/circles.png "IndicatorView circles")](indicatorview-images/circles-large.png#lightbox "IndicatorView circles")

`IndicatorView` is available in Xamarin.Forms 4.4. However, it's currently experimental and can only be used by adding the following line of code to your `AppDelegate` class on iOS, or to your `MainActivity` class on Android, before calling `Forms.Init`:

```csharp
Forms.SetFlags("IndicatorView_Experimental");
```

`IndicatorView` defines the following properties:

- `Count`, of type `int`, the number of indicators.
- `HideSingle`, of type `bool`, determines whether to hide the indicator when there's only one. The default value is `true`.
- `IndicatorColor`, of type `Color`, the color of the indicators.
- `IndicatorSize`, of type `double`, the size of the indicators. The default value is 6.0.
- `IndicatorLayout`, of type `Layout<View>`,  . This property is the content property of the `IndicatorView` class, and therefore does not need to be explicitly set.
- `IndicatorTemplate`, of type `DataTemplate`, the template to render on the indicator.
- `IndicatorsShape`, of type `IndicatorShape`, the shape to render for each indicator.
- `ItemsSource`, of type `IEnumerable`, the collection that indicators will be displayed for. Note that this property will automatically be set when the `ItemsSourceBy` property is set.
- `ItemsSourceBy`, of type `VisualElement`, the `CarouselView` object to display indicators for.
- `MaximumVisible`, of type `int`, the maximum number of visible indicators. The default value is `int.MaxValue`.
- `Position`, of type `int`, the current selected indicator index. This property uses a `TwoWay` binding.
- `SelectedIndicatorColor`, of type `Color`, the color of the indicator that shows the selected item.

These properties are backed by [`BindableProperty`](xref:Xamarin.Forms.BindableProperty) objects, which means that they can be targets of data bindings, and styled.

## Create an IndicatorView

The following example shows how to instantiate an `IndicatorView` in XAML:

```xaml
<StackLayout>
    <CarouselView x:Name="carouselView"
                  ItemsSource="{Binding Monkeys}">
        <CarouselView.ItemTemplate>
            <!-- DataTemplate that defines item appearance -->
        </CarouselView.ItemTemplate>
    </CarouselView>
    <IndicatorView ItemsSourceBy="carouselView"
                   IndicatorColor="LightGray"
                   SelectedIndicatorColor="DarkGray"
                   Margin="0,0,0,40"
                   HorizontalOptions="Center" />
</StackLayout>
```

In this example, the `IndicatorView` is rendered beneath the `CarouselView`, with an indicator for each item in the `CarouselView`. The `IndicatorView` is populated with data by setting the `ItemsSourceBy` property to the `CarouselView` object. Setting this property results in the `Position` property binding to the `CarouselView.Position` property, and the `ItemsSource` property binding to the `CarouselView.ItemsSource` property.

Each indicator is light gray, while the indicator that represents the currently displayed item in the `CarouselView` is dark gray.

## Change indicator shape

The `IndicatorView` class has a `IndicatorsShape` property, which indicates the shape of the indicators. This property should be set to one of the `IndicatorShape` enumeration members:

- `Circle` specifies that the indicator shapes will be circular. This is the default value of the `IndicatorView.IndicatorsShape` property.
- `Square` indicates that the indicator shapes will be square.

The following example shows an `IndicatorView` configured to use square indicators:

```xaml
<IndicatorView IndicatorsShape="Square"
               ItemsSourceBy="carouselView"
               IndicatorColor="LightGray"
               SelectedIndicatorColor="DarkGray" />
```

## Related links

- [IndicatorView (sample)](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-indicatorviewdemos/)
