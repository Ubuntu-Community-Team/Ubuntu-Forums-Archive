---
title: "Can I use xfce4 .xml keybindings file with openbox?"
date: 2015-11-05
forum: Programming Talk
---

### Post by Bucky Ball on 2015-11-05
Hi all,

I'm a bit of a stranger in this area, know little about programming, but figured I may get the quickest response here. I've been digging about, but can't find an answer to my question quite specific enough.

I have a minimal install running xfce4 and have added many keyboard shortcuts using the 'Application Shortcuts' under Keyboard in the Settings menu. I'm fooling with openbox and wondering how/if I can use those in openbox without having to redo all of them (I launch just about everything from the keyboard and like to avoid the mouse). 

I found where the keybindings are kept for xfce4 and openbox and they are both xml files, but the contents are 'scripted' differently? In an openbox session at /.config/openbox/rc.xml:

```
<keybind key="W-e">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Konqueror</name>
        </startupnotify>
        <command>kfmclient openProfile filemanagement</command>
      </action>
</keybind>
```

First question, call it a quick detour: If I had to change them, could I use the above as a template and simply change it to this:

```
<keybind key="Super-f">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>firefox</name>
        </startupnotify>
        <command>kfmclient openProfile filemanagement</command>
      </action>
</keybind>
```

? Or is there more to it? 

To continue. For xfce4 on my mini install, the keyboard shortcuts are stored at ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml and here is an example of how they look there. 

```
<property name="&lt;Super&gt;t" type="string" value="lxterminal"/>
<property name="&lt;Super&gt;m" type="string" value="pcmanfm"/>
```

My question: Is there anyway I can use the many keyboard shortcuts I have in the xfce4 xml file in the openbox boot? Can I copy/paste the contents into the openbox rc.xml file and it will be understood, or is that a ludicrously stupid suggestion? (It's okay, I said it first!) 

Thanks in advance for any help or advice re. the two languages, if that is the difference between the two files. Hoping this is a hop, skip and a jump to a solution and just my lack of knowledge because I'm liking openbox and could probably switch to it if I can get this working easily, at least for some percentage of my computing time. ;)

---

### Post by ajgreeny on 2015-11-05
Interesting question, BB.

I have a VM of Lubuntu which uses openbox so tried it to see what happened, making sure I had a snapshot of the VM in case everything went to worms.

I added the xfce4 xml file contents to the ~/.config/openbox/rc.xml and tried a logout and in again.  I deleted the openbox keyboard content from the file in a first try and left all the content in for a second try

Unfortunately it made no difference in either case to the keyboard actions/shortcuts other then removing all shortcuts in the first try when the openbox keyboard content was removed. 

This is a pity as setting up keyboard shortcuts, which I use a great deal in Xubuntu, and which is dead easy in xfce4, is a complete and total disaster in Lubuntu/openbox, with no GUI application to do it as far as I can see and it takes so long to manually edit that rc.xml file in openbox, and is not simple to find the key codes for some of the keys I use in Xubuntu.

---

### Post by vasa1 on 2015-11-05
I didn't have too much of a problem switching from xfce to openbox around the time of 12.10 (quantal?). Maybe that's because I use a limited set of software. And I didn't attempt a copy/paste from the xfce xml file to rc.xml.

There was obkey, a GUI editor for openbox keybinds, but it seems it isn't maintained any more.

---

### Post by Bucky Ball on 2015-11-05
Thanks for the input to you both. 

ajgreeny: Thanks for trying all that. Exactly what I was thinking and wondering if that would work. Thanks to your experimentation we know it doesn't.

vasa1: Bring back obkey! I'm okay with the software, as I say, minimal install and only the apps I use/need, which isn't a lot. It's the keybindings that are holding me back at this point. Everything else is too my liking (noticeably faster and more minimal) and looks like there's tweakage to brighten things up if I ever fancy that, which is doubtful.

Interestingly, I changed the windows theme in openbox when I was fooling around. When I logged back into my xfce session, to my surprise, the changes stuck and the window theme I'd selected in openbox persisted in the xfce4 session, so it seems that file is used in both (I did that with a GUI so didn't edit a file so not sure where that's kept/or named.)

Will dig around a bit more later. Thanks again. :)

---

### Post by vasa1 on 2015-11-05
> **Bucky Ball said:**
> ...
vasa1: Bring back obkey! ...
One of my regrets is that I can't code even to save my life!

But there was a request to include obkey in Lubuntu: [https://lists.launchpad.net/lubuntu-desktop/msg05802.html](https://lists.launchpad.net/lubuntu-desktop/msg05802.html) but that went nowhere :(

If you're adventurous enough (or have a VM), this is a link to the last known build: [https://github.com/nsf/obkey](https://github.com/nsf/obkey)


> **Bucky Ball said:**
>  ... Interestingly, I changed the windows theme in openbox when I was fooling around. When I logged back into my xfce session, to my surprise, the changes stuck and the window theme I'd selected in openbox persisted in the xfce4 session, so it seems that file is used in both (I did that with a GUI so didn't edit a file so not sure where that's kept/or named.)

Will dig around a bit more later. Thanks again. :)

I'm totally out of touch with xfwm4 but the GUI program to change a lot of settings (other than keybinds and mousebinds, etc) in Openbox is called ObConf and that is a "recommend" of the Openbox package:
```
Depends: libc6 (>= 2.4), libglib2.0-0 (>= 2.35.9), libice6 (>= 1:1.0.0), libobrender29 (>= 3.5.2), libobt2 (>= 3.5.2), libsm6, libstartup-notification0 (>= 0.7), libx11-6, libxau6, libxext6, libxi6 (>= 2:1.2.99.4), libxinerama1, libxrandr2
Recommends: **obconf**, python-xdg
```

The file it writes to is ~/.config/openbox/rc.xml (or lubuntu-rc.xml or lxde-rc.xml).```
  <theme><name>AAA111</name><titleLayout>L</titleLayout><!--
      available characters are NDSLIMC, each can occur at most once.
      N: window icon
      L: window label (AKA title).
      I: iconify
      M: maximize
      C: close
      S: shade (roll up/down)
      D: omnipresent (on all desktops).
--><keepBorder>no</keepBorder> #changed to "no" on 21/4/2014
    <animateIconify>no</animateIconify>
    <font place="ActiveWindow"><name>Ubuntu Medium</name><size>12</size><!-- font size in points --><weight>bold</weight><!-- 'bold' or 'normal' --><slant>normal</slant><!-- 'italic' or 'normal' --></font>
    <font place="InactiveWindow"><name>Ubuntu Medium</name><size>12</size><!-- font size in points --><weight>bold</weight><!-- 'bold' or 'normal' --><slant>normal</slant><!-- 'italic' or 'normal' --></font>
    <font place="MenuHeader"><name>Ubuntu</name><size>12</size><!-- font size in points --><weight>bold</weight><!-- 'bold' or 'normal' --><slant>normal</slant><!-- 'italic' or 'normal' --></font>
    <font place="MenuItem"><name>Ubuntu mono</name><size>14</size><!-- font size in points --><weight>normal</weight><!-- 'bold' or 'normal' --><slant>normal</slant><!-- 'italic' or 'normal' --></font>
    <font place="ActiveOnScreenDisplay"><name>Ubuntu Medium</name><size>12</size><!-- font size in points --><weight>bold</weight><!-- 'bold' or 'normal' --><slant>normal</slant><!-- 'italic' or 'normal' --></font>
    <font place="InactiveOnScreenDisplay"><name>Ubuntu Medium</name><size>12</size><!-- font size in points --><weight>bold</weight><!-- 'bold' or 'normal' --><slant>normal</slant><!-- 'italic' or 'normal' --></font>
  </theme>
```So, one can avoid installing Obconf and just edit the file directly and then run **openbox --reconfigure** to make the changes effective.

Openbox reads *~/.themes/theme_name/openbox-3/themerc* or */usr/share/themes/theme_name/openbox-3/themerc*.

I can't explain why xfwm4 was seeing the Openbox decorations.

---

### Post by vasa1 on 2015-11-06
Well, I downloaded obkey from [https://code.google.com/p/obkey/downloads/detail?name=obkey-1.0.tar.gz](https://code.google.com/p/obkey/downloads/detail?name=obkey-1.0.tar.gz) and I extracted in my home folder and ran it from there using **./obkey**. It seems to work on my system (Openbox session of Lubuntu 14.04.3 64-bit).

I still prefer editing rc.xml directly ;)

---

