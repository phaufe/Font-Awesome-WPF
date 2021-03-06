# Font-Awesome-WPF

WPF controls for the iconic font and CSS toolkit Font Awesome.

Font Awesome: http://fortawesome.github.io/Font-Awesome/
- Current Version: v4.2

## Getting started

### Install

To install FontAwesome.WPF, run the following command in the Package Manager Console:
```
PM> Install-Package FontAwesome.WPF
```

Or search & install the package via the NuGet Package Manager.


### Usage XAML

```
<Window x:Class="Example.FontAwesome.WPF.Single"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:fa="clr-namespace:FontAwesome.WPF;assembly=FontAwesome.WPF"
        Title="Single" Height="300" Width="300">
    <Grid  Margin="20">
        <fa:ImageAwesome Icon="Flag" VerticalAlignment="Center" HorizontalAlignment="Center" />
    </Grid>
</Window>
```

You can also use the TextBlock based control.
```
<fa:FontAwesome Icon="Flag" />
```

> The Image based <fa:ImageAwesome /> control is useful when you need to fill an entire space. Whereas the TextBlock base <fa:FontAwesome /> is advantages when you need a certain FontSize. 

#### Binding

The Icon Property is a DependencyProperty so it can be used with-in a {Binding}. There is an example in the example project.


### Usage Code-Behind

If you want to create an Image from Code-Behind (e.g. setting the Window.Icon):

```C#
Icon = ImageAwesome.CreateImageSource(FontAwesomeIcon.Flag, Brushes.Black);
```

## WPF Example

![alt text](/doc/screen-example.png "Example")

Can be found in /example/ folder.

## Icons

All icons including their aliases are generated from FontAwesomes' icons.yaml. 

```C#
public enum FontAwesomeIcon {
....
///<summary>cog (created: 1.0)</summary>
///<see cref="http://fontawesome.io/icon/cog/" />
[IconCategory("Web Application Icons"),IconCategory("Spinner Icons")]
[Description("cog")]
Cog = 0xf013,
///<summary>Alias of: Cog</summary>
///<see cref="F:FontAwesome.WPF.FontAwesomeIcon.Cog" />
[IconAlias]
Gear = Cog,
....
}
```

Following meta data is added:
* Icon
	* XML-Doc <summary> from name with created reference.
	* XML-DOC <see /> for direct link to icon web page.
	* IconCategory Attributes, one per category
	* Description Attribute, name
* Alias
	* XML-Doc <summary> Alias of: referencing icon
	* XML-Doc <see /> to referencing field (to reduce code file length)
	* IconAlias Attribute