---
title: "Noob Seeks to Have Perfect Fonts. Seeks Help from the Master"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by Danny_Michel on 2013-10-27
Hello all,


I've been messing around with my fonts since I started using Linux, which was about 2 weeks ago, so I' m quite a noob. Googling around has always brought me to this forum, so I'm seeking help here. I know you guys use Infinality, which I've tried, but I'm not 100% sure if that's the route I need to go, because I've tried it. I've installed it by adding the PPA then doing sudo apt-get. Installed it and used custom settings, but could never get the desired results.
    I love Linux, and I know font's display ever nicer than they do on OS X, but I want too achieve the OS X font rendering on here. I know there is an Infinality setting for OS X, but it doesnt come close.
    I like the way Linux fonts can be axtremely smooth and sharp, but I've gotten use to the slight imperfectness of OS X fonts that isbest described on Linux as zero hinting, but still sharp. what i've done without using Infinality is set up /etc/fonts/local.conf as you see it below. I'm pretty sure OS X doesnt use RGB.
    What I get with that is very similar to OS X, but its slightly blurrier as you can see from the first screenshot bellow, and fonts like Helvetica are more rounded and vertically smaller from the second twitter screenshot bellow. You might say to use slight hinting on Linux to make it slightly sharper, but that isnt true. It changes the shape way to much when using slight hinting and it goes a little overboard.


Thanks in advance for any help.


Sharper on OS X
[IMG]http://i.imgur.com/Chgz6Ld.png[/IMG]
See where is says 'View summary'?
[IMG]http://i.imgur.com/KKAzzLB.png[/IMG]


```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
  <match target="font" >
    <edit mode="assign" name="autohint">  <bool>true</bool></edit>
    <edit mode="assign" name="hinting">      <bool>false</bool></edit>
    <edit mode="assign" name="lcdfilter"> <const>lcdlight</const></edit>
    <edit mode="assign" name="hintstyle"> <const>hintslight</const></edit>
    <edit mode="assign" name="antialias"> <bool>true</bool></edit>
    <edit mode="assign" name="rgba">      <const>none</const></edit>
  </match>


  <match target="font">
    <test name="pixelsize" qual="any" compare="more"><double>15</double></test>
    <edit mode="assign" name="lcdfilter"><const>lcdlight</const></edit>
    <edit mode="assign" name="hintstyle"><const>hintnone</const></edit>
  </match>


  <match target="font">
    <test name="weight" compare="more"><const>medium</const></test>
    <edit mode="assign" name="hintstyle"><const>hintnone</const></edit>
    <edit mode="assign" name="lcdfilter"><const>lcdlight</const></edit>
  </match>


  <match target="font">
    <test name="slant"  compare="not_eq"><double>0</double></test>
    <edit mode="assign" name="hintstyle"><const>hintnone</const></edit>
    <edit mode="assign" name="lcdfilter"><const>lcdlight</const></edit>
  </match>


</fontconfig>
```

---

