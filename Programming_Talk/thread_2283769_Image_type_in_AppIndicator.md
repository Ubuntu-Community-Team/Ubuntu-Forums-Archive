---
title: "Image type in AppIndicator"
date: 2015-06-24
forum: Programming Talk
---

### Post by liam24 on 2015-06-24
Hey gang. I posted this in another sub but don't think it was the correct one.

I have an AppIndicator that's running fine only I can't seem to set the icon of the indicator.
I'm wondering if I'm missing something completely obvious.

```
app_indicator_set_icon_theme_path(indicator, "./path/to/icon.png"); //no good
app_indicator_set_icon_theme_path(indicator, "~a/really/long/absolute/path/to/icon.png"); //no good
```

As said, I'm pretty sure this is all I need to change the image but the  documentation does not make it clear... I'm not sure I'm even using the  correct format.

Any assistance is appreciated.

Liam

---

### Post by ofnuts on 2015-06-25
[FONT=lucida sans unicode][/FONT]First, "~a/really/long/absolute/path/to/icon.png" is not an absolute path, it's a relative path that starts with a directory named "~a" in your current directory. "~" substitution is done by the script shells not by filesystems or system calls.

Second, app_indicator_set_icon_theme_path() expect a directory too look for icons, not an icon. So I assume you give a directory there, and then just an icon name in other calls that set the icon.

---

### Post by liam24 on 2015-06-25
> **ofnuts said:**
> e]app_indicator_set_icon_theme_path() expect a directory too look for icons, not an icon. So I assume you give a directory there, and then just an icon name in other calls that set the icon.

This is correct. My mistake.
I'm still unclear as to whether or not I'm feeding this function a relative path or an absolute path and I've not found what type of file it's looking for.

---

### Post by ofnuts on 2015-06-25
> **liam24 said:**
> This is correct. My mistake.
I'm still unclear as to whether or not I'm feeding this function a relative path or an absolute path and I've not found what type of file it's looking for.
I would expect it to work with both, but using a relative path requires confidence that no other part of the process is going to change the working directory.

---

### Post by liam24 on 2015-06-25
Thanks for the replies, ofnuts.

**app_indicator_set_icon_theme_path**must take an absolute path.
 Followed by **app_indicator_set_icon_full** to set the icon name. The icon filetype takes a PNG. AFAIK any size of PNG will do. Appindicator takes care of sizing.

Here's what worked for me:
```

app_indicator_set_icon_theme_path(indicator, "/home/myusername/Absolute/Path/To/My/Resource/"); // preferably you would have a relative path and a method to convert that to an absolute. This path, obviously, will not be the same on other people's machines.
app_indicator_set_icon_full(indicator, "IconFileName", "Description"); //do not include the file extension in the file's name 
```

Hoping this helps someone in the future.

---

### Post by PaulW2U on 2015-06-25
Please use default fonts wherever possible. Some users might find it difficult to read non-standard fonts and font-sizes.

---

