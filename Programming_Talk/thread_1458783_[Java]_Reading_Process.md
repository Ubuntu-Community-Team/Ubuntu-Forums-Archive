---
title: "[Java] Reading Process"
date: 2010-04-20
forum: Programming Talk
---

### Post by arvigeus on 2010-04-20
Hello! I'm trying to write a program to control the display using xrandr. My question is how to read values from the output. Example:
```
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0*+
   640x480        59.9
```

And here is what I done so far:
```
private static  int[] minimum = new int[2];
	private static  int[] current = new int[2];
	private static  int[] maximum = new int[2];
	private String[] output = new String[2];
	private TreeMap <Integer, Integer>supported = new TreeMap<Integer, Integer>();
public static void detect() {
		Process proc=Runtime.getRuntime().exec("xrandr -q");
		InputStream reader=proc.getInputStream();
		StringBuilder builder = new StringBuilder();
		int c;
		while((c = reader.read()) != -1) builder.append((char)c);
		String device = new String(builder.toString());
		String sub = new String();
		sub=device.substring(device.indexOf("minimum"+8, device.indexOf(", current")-1));
		minimum[0] = Integer.parseInt(sub.substring(0, sub.indexOf('x')-1));
		minimum[1] = Integer.parseInt(sub.substring(sub.indexOf('x')+1, sub.length()));
		sub=device.substring(device.indexOf("current"+8, device.indexOf(", maximum")-1));
		current[0] = Integer.parseInt(sub.substring(0, sub.indexOf('x')-1));
		current[1] = Integer.parseInt(sub.substring(sub.indexOf('x')+1, sub.length()));
		}
```

Easiest way is to separate it to different lines (maybe with another TreeMap?) and this probably is the hardest part, but don't know how to do it.

What *(normal left inverted right x axis y axis)* stands for and which are the variables here? And the last two lines are the supported resolutions, * is current, but what is + ?

---

### Post by geirha on 2010-04-20
Unfortunately, xrandr output is not designed to be parsed, it's designed to be human readable. That doesn't necessarily mean it's not possible to parse, but it does mean it'll be hard to parse it.

I did a quick search for «java xrandr» and found a java library with an XRandR class. I peeked at the code, and it does run xrandr -q and parses the output, so that should give you some ideas on how to do it.

[http://lwjgl.org/javadoc/org/lwjgl/opengl/XRandR.html](http://lwjgl.org/javadoc/org/lwjgl/opengl/XRandR.html)
[http://lwjgl.org/](http://lwjgl.org/)

Make sure you check the license of that code so you don't violate it.

---

### Post by myrtle1908 on 2010-04-20
I'm not sure exactly what you are trying to grab from that output.

The following example uses the Java regex lib and grabs Screen 0 minimum width and height.  I'm sure you figure out the rest.

```
import java.util.regex.Pattern;
import java.util.regex.Matcher;
public class Test {
	public static void main(String[] args) {
		String s = "Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096";
		Pattern minimum = Pattern.compile("minimum\\s+(\\d+)\\s+x\\s+(\\d+)", Pattern.CASE_INSENSITIVE);
		Matcher m = minimum.matcher(s);
		int w = 0;
		int h = 0;
		if (m.find()) {
			// you may also like to check m.group.length() for safety
			w = Integer.parseInt(m.group(1));
			h = Integer.parseInt(m.group(2));
		}
		System.out.println("w=" + w + "\nh=" + h);
	}
}

```

---

### Post by arvigeus on 2010-04-21
Thank you all!
I think I'm gonna use simple lwjgl.XRandR. I actually yesterday I figured out that I can split new lines into dynamic array and read them with substring() and blind searching. Now it will go easier just to get all needed things directly from this predefined class.
Now how to import/use this?...

---

