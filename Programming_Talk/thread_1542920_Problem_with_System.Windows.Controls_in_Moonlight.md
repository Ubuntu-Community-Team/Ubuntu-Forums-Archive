---
title: "Problem with System.Windows.Controls in Moonlight"
date: 2010-07-31
forum: Programming Talk
---

### Post by Newbie2910 on 2010-07-31
I get this error message:
Could not parse element WrapPanel, attribute (null), error: Unable to resolve managed type WrapPanel

When my Moonlight app starts up. 

I have the namespace set up:
xmlns:basics="clr-namespace:System.Windows.Controls;assembly=System.Windows.Controls" at the top of my Xaml and I have a reference set to:
System.Windows.Controls

Here's how the WrapPanel is defined:
                <basics:WrapPanel Orientation="Vertical" Margin="-2,2,0,0" Background="White" Name="RightGridStackPanel" VerticalAlignment="Top" Height="Auto">
                        
I get a similar error when referencing any other of the controls that are in that assembly (like ListView).

What am I missing?

---

