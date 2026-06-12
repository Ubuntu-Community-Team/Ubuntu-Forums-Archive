---
title: "Warning: Cannot convert string to type FontStruct Problem"
date: 2008-05-14
forum: Programming Talk
---

### Post by Sequences on 2008-05-14
I have finally solved the problem I had earlier with blank windows by upgrading my JRE to Java6. But I am still plagued by this problem:
```
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-wenquanyi-wenquanyi zenhei-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct
```

Tried looking it up, but just got a bunch of foreign websites. Tried to follow some other directions to look for a font.alias, but that turned up nothing. Was wondering if anyone knows of this.

---

### Post by sparks88 on 2009-05-02
Are you running with desktop effects on? If so try putting this in your a login file (like ~/.profile). 
```
export AWT_TOOLKIT=MToolkit
```
Also try turning off desktop effects and see if that fixes it.

If not you're in the same boat I am. Here are some similar threads I've found:
[http://ubuntuforums.org/showthread.php?t=926949&highlight=FontStruct](http://ubuntuforums.org/showthread.php?t=926949&highlight=FontStruct)
[http://ubuntuforums.org/showthread.php?t=793192&highlight=FontStruct](http://ubuntuforums.org/showthread.php?t=793192&highlight=FontStruct)

---

