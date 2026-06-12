---
title: "Type mismatches in tweaked Inkscape extensions"
date: 2010-04-17
forum: Programming Talk
---

### Post by Shnatsel on 2010-04-17
I'm trying to mix two Inkscape extensions: 'More hue', which is not interactive and therefore barely usable, and 'Replace color', which has a UI. I want to get an interactive hue tweaking tool. Here's what I got out of mixing them:

**hue_tweak.inx**
```
<?xml version="1.0" encoding="UTF-8"?>
<inkscape-extension xmlns="http://www.inkscape.org/namespace/inkscape/extension">
	<_name>Tweak hue</_name>
	<id>org.inkscape.color.tweakhue</id>
	<dependency type="executable" location="extensions">coloreffect.py</dependency>
	<dependency type="executable" location="extensions">hue_tweak.py</dependency>
	<dependency type="executable" location="extensions">simplestyle.py</dependency>
	<param name="val" type="string" max_length="3" _gui-text="Hue change (-100 to 100):">0</param>
	<effect>
		<object-type>all</object-type>
		<effects-menu>
			<submenu _name="Color"/>
		</effects-menu>
	</effect>
	<script>
		<command reldir="extensions" interpreter="python">hue_tweak.py</command>
	</script>
</inkscape-extension>
```


**hue_tweak.py**
```
import coloreffect

import inkex

class C(coloreffect.ColorEffect):
  def __init__(self):
    coloreffect.ColorEffect.__init__(self)
    self.OptionParser.add_option("-v", "--val", action="store", type="string", dest="val", default="0", help="Hue change (-100 to 100)")

  def colmod(self,r,g,b):
    hsl = self.rgb_to_hsl(r/255.0, g/255.0, b/255.0)

    value = int(self.options.val)
    hsl[0] = hsl[0] + (value / 100.0)
    if hsl[0] > 1.0:
	hsl[0] = hsl[0] - 1.0
    rgb = self.hsl_to_rgb(hsl[0], hsl[1], hsl[2])

c = C()
c.affect()
```

And I get a type mismatch:
```
Traceback (most recent call last):
  File "/usr/share/inkscape/extensions/hue_tweak.py", line 20, in <module>
    c.affect()
  File "/usr/share/inkscape/extensions/inkex.py", line 207, in affect
    self.effect()
  File "/usr/share/inkscape/extensions/coloreffect.py", line 39, in effect
    self.getAttribs(node)
  File "/usr/share/inkscape/extensions/coloreffect.py", line 42, in getAttribs
    self.changeStyle(node)
  File "/usr/share/inkscape/extensions/coloreffect.py", line 80, in changeStyle
    new_val = self.process_prop(val)
  File "/usr/share/inkscape/extensions/coloreffect.py", line 98, in process_prop
    self.process_gradient(node, newid)
  File "/usr/share/inkscape/extensions/coloreffect.py", line 127, in process_gradient
    self.process_gradient(node, newhref)
  File "/usr/share/inkscape/extensions/coloreffect.py", line 116, in process_gradient
    self.changeStyle(child)
  File "/usr/share/inkscape/extensions/coloreffect.py", line 80, in changeStyle
    new_val = self.process_prop(val)
  File "/usr/share/inkscape/extensions/coloreffect.py", line 90, in process_prop
    col='#'+self.colmod(c[0],c[1],c[2])
TypeError: cannot concatenate 'str' and 'NoneType' objects

```

What am I doing wrong? Is there any way to fix this?

---

