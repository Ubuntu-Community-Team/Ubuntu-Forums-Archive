---
title: "HOWTO: Disable antialiasing for some font-sizes"
date: 2004-11-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Julius on 2004-11-06
This will work to disable antialiasing for fonts that are using a size less than 9 or 10.
In windows, some font sizes (I think from 6 to 8) are never antialiased, because they would look too blurry. In kde there's an option to avoid antialising for some fontsizes, and you can do the same for gnome editing a simple file.
With this, webpages using small fonts (8pt) will look clearer. Of course, all fonts in your system with that size will look without antialiasing. 

Edit your /etc/fonts/local.conf with root priviledges (sudo nano /etc/fonts/local.conf). I think you can also create a file in your home directory called ./fonts.com, but I'm not sure of this.


Add the following to that file (inside the XML tree)
```

        <match target="pattern">
                <test qual="any" name="size" compare="less">
                        <double>10</double>
                </test>
                <edit name="antialias" mode="assign">
                        <bool>false</bool>
                </edit>
        </match>
        <match target="pattern">
                <test qual="any" name="pixelsize" compare="less">
                        <double>14</double>
                </test>
                <edit name="antialias" mode="assign">
                        <bool>false</bool>
                </edit>
        </match>

```

Some applications ignore "size" and use "pixelsize" instead. 
Fonts equal or smaller than 9-10px (I'm still not sure: try changing the values between the <double> labels.)  should show without any antialising.

---

