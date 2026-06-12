---
title: "Accidentally deleted fonts.conf file, how do I restore it?"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by EGE-FB on 2008-06-02
Hi, 

I was messing around with the fonts on my system and I accidentally managed to remove the .fonts.conf file in the /etc/fonts/ directory.. Now my fonts are out of whack (for example the default font on my system looks like Times New Roman even though it is "Sans").. How do I fix this without having to reinstall the whole operating system? How can I restore the file or replace it?

Thanks

---

### Post by sports fan Matt on 2008-06-02
Is it still in your trash folder?

---

### Post by EGE-FB on 2008-06-02
No I dont think it was ever in my trash folder.. (I deleted it using terminal.. using the "rm" command).. 

Please help =)

---

### Post by kerry_s on 2008-06-02
open the fonts settings and change something, it will make a new one.
or
you can just make it yourself.

i make my own cause i use a custom install.

mine:

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Helvetica</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Verdana</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Arial</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Lucida</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Times</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Roman</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Courier</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Mono</string>
 </edit>
</match>

</fontconfig>


```

---

### Post by EGE-FB on 2008-06-02
could someone provide an untouched "default" fonts.conf file that I could use to put into the /etc/fonts/ folder?

thanks

---

### Post by kerry_s on 2008-06-02
> **EGE-FB said:**
> could someone provide an untouched "default" fonts.conf file that I could use to put into the /etc/fonts/ folder?

thanks

oh you need that one. attached. :)

---

### Post by t.rei on 2008-08-08
Hm... I could use the whole default "etc/fonts/" folder. :/ Sometimes I still trust step-by-step howto's too much so I ended up with a garbled config. 

Thanks in advance.

---

### Post by victorhugo289 on 2011-02-17
> **kerry_s said:**
> open the fonts settings and change something, it will make a new one.
or
you can just make it yourself.

i make my own cause i use a custom install.


You guys just solved one little issue that's been bugging me for about a month. I didn't know about this file ".fonts.conf", deleting it made wonders!
Since I installed Kubuntu and shared the /home partition there were issues with the fonts, particularly Firefox had a KDE look that with a very thin font that I didn't like, now it's all back to normal.
Whew! at last! \\:D/

(And I don't share the /home partition between distros anymore.)

---

### Post by peleh on 2011-06-27
Can someone please reupload the default .font.conf, i deleted accidentally too.. :popcorn:

Edit: Nevermint, grabbed the contents from the /etc/fonts folder.

---

