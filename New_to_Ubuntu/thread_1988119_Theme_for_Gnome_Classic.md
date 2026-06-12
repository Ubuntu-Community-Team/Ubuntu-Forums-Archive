---
title: "Theme for Gnome Classic"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by traditionalist on 2012-05-26
Since lots of people were asking about this, I built this theme for Gnome Classic on 12.04.

It alters firefox and thunderbird as well as all software that can use the system default theme.

You can apply it and tweak it, or build your own, using this;

[[IMG]http://img820.imageshack.us/img820/851/ubuntusoftwarecenter003.th.png[/IMG]]("http://img820.imageshack.us/i/ubuntusoftwarecenter003.png/")

You can also revert or alter at any time. Changes take effect on the system more or less immediately, depending on how fast your system is,  they are also shown in the panel you are working  in, and you can see what happens to other windows  if you keep a couple of windows open. Most well behaved system programs will accept the changes immediately. Some changes, especially for firefox and similar programs, will only take effect after you restart firefox. This is the actual theme being set up;

[[IMG]http://img51.imageshack.us/img51/5656/gnomecolorchooser004.th.png[/IMG]]("http://img51.imageshack.us/i/gnomecolorchooser004.png/")


This is the xml output if you save the theme. DO NOT put the result in a folder named "Themes"  this causes problems. Call the folder you save it to "Systemcolors" or something like that.

It is quite easy to use, even by a complete beginner. It produces xml  output like this;

```
<?xml version="1.0" encoding="UTF-8"?>
<theme>

  <!-- Category: default -->
    <!-- Element: bg[NORMAL] -->
  <element id ="0" value="#2D2C2B"/>
    <!-- Element: bg[PRELIGHT] -->
  <element id ="1" value="#FFFFFF"/>
    <!-- Element: bg[SELECTED] -->
  <element id ="2" value="#FFFFFF"/>
    <!-- Element: bg[ACTIVE] -->
  <element id ="3" value="#0000FF"/>
    <!-- Element: bg[INSENSITIVE] -->
  <element id ="4" value="#5D5C43"/>
    <!-- Element: fg[NORMAL] -->
  <element id ="5" value="#FFFFFF"/>
    <!-- Element: fg[PRELIGHT] -->
  <element id ="6" value="#928C18"/>
    <!-- Element: fg[SELECTED] -->
  <element id ="7" value="#E61D1D"/>
    <!-- Element: fg[ACTIVE] -->
  <element id ="8" value="#50CC25"/>
    <!-- Element: fg[INSENSITIVE] -->
  <element id ="9" value="#F209A3"/>
    <!-- Element: base[NORMAL] -->
  <element id ="10" value="#999999"/>
    <!-- Element: base[PRELIGHT] -->
  <element id ="11" value="#FFE800"/>
    <!-- Element: base[SELECTED] -->
  <element id ="12" value="#EE1111"/>
    <!-- Element: base[ACTIVE] -->
  <element id ="13" value="#0000FF" disabled="true"/>
    <!-- Element: base[INSENSITIVE] -->
  <element id ="14" value="#E8DA14"/>
    <!-- Element: text[NORMAL] -->
  <element id ="15" value="#1F11FA"/>
    <!-- Element: text[PRELIGHT] -->
  <element id ="16" value="#0600FF"/>
    <!-- Element: text[SELECTED] -->
  <element id ="17" value="#FFFFFF"/>
    <!-- Element: text[ACTIVE] -->
  <element id ="18" value="#F69516"/>
    <!-- Element: text[INSENSITIVE] -->
  <element id ="19" value="#3B4228"/>
    <!-- Element: xthickness -->
  <element id ="20" value="3"/>
    <!-- Element: ythickness -->
  <element id ="21" value="3"/>
    <!-- Element: bg_pixmap[NORMAL] -->
  <element id ="56" value="&lt;none&gt;"/>
    <!-- Element: bg_pixmap[PRELIGHT] -->
  <element id ="57" value="&lt;none&gt;"/>
    <!-- Element: bg_pixmap[INSENSITIVE] -->
  <element id ="60" value="&lt;none&gt;"/>
    <!-- Element: GtkMenuBar::shadow_type -->
  <element id ="79" value="GTK_SHADOW_NONE"/>
    <!-- Element: GtkToolbar::shadow_type -->
  <element id ="80" value="GTK_SHADOW_NONE"/>
    <!-- Element: GtkWidget::link-color -->
  <element id ="81" value="#0000EE"/>
    <!-- Element: GtkWidget::visited-link-color -->
  <element id ="82" value="#551A8B"/>

    <!-- Engine: redmond95 -->
  <engine name="redmond95" category="default" disabled="true">
  </engine>


  <!-- Category: desktop-icon -->
    <!-- Element: NautilusIconContainer::frame_text -->
  <element id ="22" value="1"/>
    <!-- Element: text[NORMAL] -->
  <element id ="23" value="#000000"/>
    <!-- Element: base[NORMAL] -->
  <element id ="24" value="#FFFFFF"/>
    <!-- Element: NautilusIconContainer::normal_alpha -->
  <element id ="25" value="0"/>
    <!-- Element: NautilusIconContainer::normal_icon_render_mode -->
  <element id ="61" value="0"/>
    <!-- Element: NautilusIconContainer::prelight_icon_render_mode -->
  <element id ="62" value="1"/>
    <!-- Element: NautilusIconContainer::normal_icon_color -->
  <element id ="63" value="#FF0000"/>
    <!-- Element: NautilusIconContainer::prelight_icon_color -->
  <element id ="64" value="#FF00AA"/>
    <!-- Element: NautilusIconContainer::normal_icon_saturation -->
  <element id ="65" value="150"/>
    <!-- Element: NautilusIconContainer::prelight_icon_saturation -->
  <element id ="66" value="255"/>
    <!-- Element: NautilusIconContainer::normal_icon_brightness -->
  <element id ="67" value="200"/>
    <!-- Element: NautilusIconContainer::prelight_icon_brightness -->
  <element id ="68" value="255"/>
    <!-- Element: NautilusIconContainer::selection_box_color -->
  <element id ="69" value="#FF0069"/>
    <!-- Element: NautilusIconContainer::selection_box_alpha -->
  <element id ="70" value="100"/>
    <!-- Element: NautilusIconContainer::normal_icon_lighten -->
  <element id ="71" value="0"/>
    <!-- Element: NautilusIconContainer::prelight_icon_lighten -->
  <element id ="72" value="25"/>
    <!-- Element: NautilusIconContainer::activate_prelight_icon_label -->
  <element id ="73" value="1"/>
    <!-- Element: text[PRELIGHT] -->
  <element id ="74" value="#000000"/>
    <!-- Element: base[PRELIGHT] -->
  <element id ="75" value="#FFFFFF"/>
    <!-- Element: NautilusIconContainer::prelight_alpha -->
  <element id ="76" value="255"/>

    <!-- Engine: redmond95 -->
  <engine name="redmond95" category="desktop-icon" disabled="true">
  </engine>


  <!-- Category: panel -->
    <!-- Element: bg[NORMAL] -->
  <element id ="26" value="#999999"/>
    <!-- Element: bg[PRELIGHT] -->
  <element id ="27" value="#FF0000"/>
    <!-- Element: bg[SELECTED] -->
  <element id ="28" value="#FFFFFF"/>
    <!-- Element: bg[ACTIVE] -->
  <element id ="29" value="#0000FF"/>
    <!-- Element: bg[INSENSITIVE] -->
  <element id ="30" value="#EEEAB0"/>
    <!-- Element: fg[NORMAL] -->
  <element id ="31" value="#FF0000"/>
    <!-- Element: fg[PRELIGHT] -->
  <element id ="32" value="#00FF00"/>
    <!-- Element: fg[SELECTED] -->
  <element id ="33" value="#EA1515"/>
    <!-- Element: fg[ACTIVE] -->
  <element id ="34" value="#FFFF00"/>
    <!-- Element: fg[INSENSITIVE] -->
  <element id ="35" value="#DBDACC"/>
    <!-- Element: xthickness -->
  <element id ="36" value="1"/>
    <!-- Element: ythickness -->
  <element id ="37" value="1"/>
    <!-- Element: font_name -->
  <element id ="54" value="Times New Roman, Italic 16"/>
    <!-- Element: bg_pixmap[NORMAL] -->
  <element id ="55" value="&lt;none&gt;"/>

    <!-- Engine: redmond95 -->
  <engine name="redmond95" category="panel" disabled="true">
  </engine>


  <!-- Category: startmenue -->
    <!-- Element: bg[NORMAL] -->
  <element id ="201" value="#999999"/>
    <!-- Element: bg[SELECTED] -->
  <element id ="202" value="#FF0000"/>
    <!-- Element: fg[NORMAL] -->
  <element id ="203" value="#EADBDB"/>
    <!-- Element: fg[PRELIGHT] -->
  <element id ="204" value="#00FF00"/>
    <!-- Element: xthickness -->
  <element id ="211" value="1"/>
    <!-- Element: ythickness -->
  <element id ="212" value="1"/>
    <!-- Element: font_name -->
  <element id ="213" value="Times New Roman, 18"/>
    <!-- Element: bg_pixmap[NORMAL] -->
  <element id ="214" value="&lt;none&gt;"/>

    <!-- Engine: redmond95 -->
  <engine name="redmond95" category="startmenue" disabled="true">
  </engine>


  <!-- Category: window-decoration-with_compiz -->
    <!-- Element: fg[NORMAL] -->
  <element id ="38" value="#C8C8C8"/>
    <!-- Element: fg[SELECTED] -->
  <element id ="39" value="#ED0A0A"/>
    <!-- Element: bg[NORMAL] -->
  <element id ="40" value="#BBBBBB"/>
    <!-- Element: bg[SELECTED] -->
  <element id ="41" value="#E2D5BF"/>

  <!-- Category: window-decoration -->
    <!-- Element: fg[NORMAL] -->
  <element id ="42" value="#C8C8C8"/>
    <!-- Element: bg[SELECTED] -->
  <element id ="43" value="#C8C0B3"/>

  <!-- Category: scrollbar -->
    <!-- Element: bg[NORMAL] -->
  <element id ="44" value="#00BFFF"/>
    <!-- Element: bg[PRELIGHT] -->
  <element id ="45" value="#FFFFFF"/>
    <!-- Element: bg[ACTIVE] -->
  <element id ="46" value="#00DFFF"/>
    <!-- Element: GtkScrollbar::slider_width -->
  <element id ="47" value="15"/>
    <!-- Element: GtkScrollbar::stepper_size -->
  <element id ="77" value="15"/>

    <!-- Engine: redmond95 -->
  <engine name="redmond95" category="scrollbar" disabled="true">
  </engine>


  <!-- Category: progressbar -->
    <!-- Element: bg[SELECTED] -->
  <element id ="48" value="#ABE120"/>
    <!-- Element: xthickness -->
  <element id ="49" value="1"/>
    <!-- Element: ythickness -->
  <element id ="50" value="1"/>

    <!-- Engine: redmond95 -->
  <engine name="redmond95" category="progressbar" disabled="true">
  </engine>


  <!-- Category: tooltips -->
    <!-- Element: bg[NORMAL] -->
  <element id ="51" value="#FFFFAF"/>
    <!-- Element: fg[NORMAL] -->
  <element id ="78" value="#000000"/>

    <!-- Engine: redmond95 -->
  <engine name="redmond95" category="tooltips" disabled="true">
  </engine>


  <!-- Category: button -->
    <!-- Element: xthickness -->
  <element id ="52" value="2"/>
    <!-- Element: ythickness -->
  <element id ="53" value="1"/>
    <!-- Element: bg[NORMAL] -->
  <element id ="83" value="#999999"/>
    <!-- Element: bg[PRELIGHT] -->
  <element id ="84" value="#FF0000"/>
    <!-- Element: bg[SELECTED] -->
  <element id ="85" value="#FFFFFF"/>
    <!-- Element: bg[ACTIVE] -->
  <element id ="86" value="#0000FF"/>
    <!-- Element: bg[INSENSITIVE] -->
  <element id ="87" value="#EEEAB0"/>
    <!-- Element: fg[NORMAL] -->
  <element id ="88" value="#200808"/>
    <!-- Element: fg[PRELIGHT] -->
  <element id ="89" value="#00FF00"/>
    <!-- Element: fg[ACTIVE] -->
  <element id ="91" value="#FFFF00"/>
    <!-- Element: fg[INSENSITIVE] -->
  <element id ="92" value="#DBDACC"/>
    <!-- Element: font_name -->
  <element id ="93" value="Arial 16"/>

    <!-- Engine: redmond95 -->
  <engine name="redmond95" category="button" disabled="true">
  </engine>


  <!-- Category: combobox -->
    <!-- Element: text[NORMAL] -->
  <element id ="94" value="#FF0000"/>
    <!-- Element: text[PRELIGHT] -->
  <element id ="95" value="#00FF00"/>
    <!-- Element: text[ACTIVE] -->
  <element id ="97" value="#FFFF00"/>
    <!-- Element: text[INSENSITIVE] -->
  <element id ="98" value="#DBDACC"/>

  <!-- Category: _TOPLEVEL_ -->
    <!-- Element: gtk-menu -->
  <element id ="100" value="16,16" disabled="true"/>
    <!-- Element: panel-menu -->
  <element id ="102" value="20,20" disabled="true"/>
    <!-- Element: gtk-large-toolbar -->
  <element id ="103" value="24,24" disabled="true"/>
    <!-- Element: gtk-button -->
  <element id ="104" value="20,20" disabled="true"/>
    <!-- Element: gtk-button-images -->
  <element id ="105" value="0" disabled="true"/>

</theme>

This of course is also an extremely useful reference if you want to know the codes for various elements.


```Here are a few examples of the theme on various software windows;

This is firefox using the system colors;

[[IMG]http://img827.imageshack.us/img827/114/ubuntuthemeforgnomeclas.th.png[/IMG]]("http://img827.imageshack.us/i/ubuntuthemeforgnomeclas.png/")

and with a few drop down menus;

[[IMG]http://img138.imageshack.us/img138/114/ubuntuthemeforgnomeclas.th.png[/IMG]]("http://img138.imageshack.us/i/ubuntuthemeforgnomeclas.png/")


[[IMG]http://img405.imageshack.us/img405/2264/selection005g.th.png[/IMG]]("http://img405.imageshack.us/i/selection005g.png/")

I hope I can attach the theme itself here! I have never tried to attach anything before. If not I will upload it to a hoster. I will attach it as a .tar.gz file.

So that was it I think. Have fun!

---

