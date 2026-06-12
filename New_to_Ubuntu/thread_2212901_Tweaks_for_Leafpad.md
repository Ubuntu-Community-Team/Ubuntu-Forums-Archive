---
title: "Tweaks for Leafpad"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by Kevin McCready on 2014-03-23
I love leafpad, but try as I might, I cannot tweak it. I do not have the skills yet and have had no luck contacting the developer who has probably gone on to higher things.

My problem right now is I need to cut and paste with ASCII only.
For example, if I cut and paste Or&#257;kei I can no longer find it as Orakei.

Any help would be appreciated. I'd also be happy to pay a budding young developer to solve the problem.

---

### Post by bapoumba on 2014-03-23
Could you save the file with ISO-8859-1 encoding ?
File > save > bottom right > character coding.

---

### Post by Kevin McCready on 2014-03-23
I got message 
Can't convert codeset to 'ISO-8859-1'
But would doing that also wipe out the unicode stuff in my file that I do want to keep? eg &#20013;&#25991;

---

### Post by bapoumba on 2014-03-24
Maybe have a look here :
[http://ubuntuforums.org/showthread.php?t=2148928](http://ubuntuforums.org/showthread.php?t=2148928)

Maybe Leafpad does not support the particular character encoding you are using ?
Have you tried other editors (gedit for ex) ?

---

### Post by Kevin McCready on 2014-03-24
Thanks Bapoumba
Leafpad certainly does support the character encoding. In fact THAT is exactly my problem. I want to be able to cut and paste and NOT bring the coding with the paste, I just want to paste in ASCII. Yes, I've tried lots of other editors but they are not as powerful in handling massive files.

I really need to be able to alter the internal programming of leafpad to insert an option to paste plain text. But I have very little programming experience. I was hoping, given that this is a simple operation, that there would be a programming module I could incorporate from elsewhere.

---

### Post by bapoumba on 2014-03-24
Others will correct me, I'm not quite sure I understand correctly. By design, in Leafpad, pasting pastes unformatted text. For ex, I have highlighted some of my post above, then middle clicked to paste. ctrl-v does the same thing. It did paste plain text, without the formatting (ie the link, the bold format etc.).

Are these files created on Windows ?

---

### Post by Kevin McCready on 2014-03-24
Maybe we are using the word formatting differently. Have you read my opening post re Orakei  Or&#257;kei ? Note that the second a has a diacritical mark. I want to be able to paste it as the first one without the diacritical mark.

---

### Post by bapoumba on 2014-03-24
> **Kevin McCready said:**
> Maybe we are using the word formatting differently. Have you read my opening post re Orakei  Or&#257;kei ? Note that the second a has a diacritical mark. I want to be able to paste it as the first one without the diacritical mark.

Yes I saw that :)
Guess I'm having a hard time reading Ops recently ;)
You want to copy the second one (with the special character) and paste it as the first one (without the special character), am I correct ?

---

### Post by Kevin McCready on 2014-03-24
Hi Thanks
Yes that's correct

---

### Post by bapoumba on 2014-03-24
Hmm, I have been looking around. My understanding is that it has to do with the copy, not the paste, or not directly. I guess it is complicated by the fact there may be a lot of special characters you want to escape and turn into the regular, not accentuated, ones. There are many tutorials on how to write or input special characters, not that I could find on how to escape them on paste.

Or have a look at iconv, that exports a file from one character encoding to another.

---

### Post by slooksterpsv on 2014-03-24
Considering the ASCII code is quite different, and Ubuntu variants support all sorts of textual options (I can copy and paste Chinese, Japanese, Russian, Korean and it won't skew or mis-convert it), you'll have to look for a program that can directly convert that for you. I don't know of one.

iconv works in terminal:
shawn@shawn-Satellite-C75D-A:~/Downloads$ echo Or&#257;kei > test.txt
shawn@shawn-Satellite-C75D-A:~/Downloads$ iconv -f UTF-8 -t ASCII//TRANSLIT ./test.txt 
Orakei

---

### Post by slooksterpsv on 2014-03-24
There I made an HTML file that you can copy the content in, click a button, and it'll do the rest. Just untar gz the file.

---

### Post by bapoumba on 2014-03-25
thanks slooksterpsv, I was thinking about something along these lines. Please see post #3, will the chinese characters be preserved ? This is what I did not know about doing.

---

### Post by slooksterpsv on 2014-03-25
Yes it looks like it just removes the accents from the characters. It didn't change the Chinese words.

---

### Post by bapoumba on 2014-03-25
> **slooksterpsv said:**
> Yes it looks like it just removes the accents from the characters. It didn't change the Chinese words.
Thanks, potential hero of the day :)

---

### Post by slooksterpsv on 2014-03-25
Tried to make a gedit plugin, it's not working too well =( - if I can get javascript to take over the handling of the conversion, that'd be great! But it's not working like that haha.

---

### Post by slooksterpsv on 2014-03-25
You are so welcome for this one, here's a plugin that will do what you want in gedit. It tooke me a few hours, but I got it =D

Just put this in your:
~/.local/share/gedit/plugins

You will need to create gedit and plugins directories

The remove diacritics is under the edit menu; sorry it's not very pretty, but it works.

EDIT: Requires gedit 3.xx and python 3 

[ATTACH]251448[/ATTACH]

[ATTACH=CONFIG]251449[/ATTACH][ATTACH=CONFIG]251450[/ATTACH][ATTACH=CONFIG]251451[/ATTACH]

---

### Post by bapoumba on 2014-03-25
That's it. Official hero of the day :)
Thanks much slooksterpsv!

---

### Post by steeldriver on 2014-03-25
... fyi I managed to get something working in Leafpad **on Ubuntu desktop** by defining a custom keyboard shortcut (I used ctrl-shift-v similar to the Windows 'paste without formatting'), with the shortcut following command

```
sh -c 'xsel -bo | iconv -t ASCII//TRANSLIT | xsel -bi && xdotool getactivewindow key ctrl+v'
```

I don't know how to define shortcuts in Openbox/LXDE

Interestingly it *doesn't* appear to workin gedit (I think applications are free to reject XSendEvent events)

---

### Post by bapoumba on 2014-03-25
Ah, you've already been my (secret) hero of the day steeldriver on other occasions, two in one day that is a lot :)
I'm at work and not on my lubuntu install. I'll have a look tonight (late, sorry). Shift-ctrl-v already pastes without formatting on Ubuntu in Libreoffice, but that is handled by the application. The shortcut is also available system wide on MacOSX. There are ways to configure keyboard shortcuts on lubuntu.

Edit : 
[https://help.ubuntu.com/community/Lubuntu/Keyboard#Create_New_Keyboard_shortcuts](https://help.ubuntu.com/community/Lubuntu/Keyboard#Create_New_Keyboard_shortcuts)
[http://openbox.org/wiki/Help:Bindings](http://openbox.org/wiki/Help:Bindings)
[http://crunchbanglinux.org/wiki/howto/edit_keyboard_shortcuts](http://crunchbanglinux.org/wiki/howto/edit_keyboard_shortcuts)
[https://wiki.archlinux.org/index.php/openbox#Keybinds](https://wiki.archlinux.org/index.php/openbox#Keybinds)

---

### Post by steeldriver on 2014-03-25
It seems to work in Lubuntu if I add

```

    <keybind key="C-A-v">
      <action name="Execute">
        <command>sh -c 'xsel -bo | iconv -t ASCII//TRANSLIT | xsel -bi &amp;&amp; xdotool getactivewindow key ctrl+v'</command>
      </action>
    </keybind>

```

to the end of the <keyboard> section of my ~/.config/openbox/lubuntu-rc.xml file. 

NB I changed the shortcut to ctrl-**alt**-v to avoid potential confusion with some terminal paste shortcuts. 
Note that the XML format of the .rc file requires the shell sequence **&&** to be escaped as **&amp;&amp;**

EDIT: you can run

```
openbox --reconfigure
```

to re-read the .rc file and make the new shortcut take effect in the current session (i.e. without having to log out and back in).

---

### Post by Kevin McCready on 2014-03-25
Thank you Steeldriver, I think that's what I'm looking for. I can define my own shortcut (I have lots already) if it clashes with others (interestingly, one of them clashes with gmail on firefox).

But before I do the sh command, which I've never done before. Could you walk me through each step so that I understand what it is I'm actually doing.

---

### Post by steeldriver on 2014-03-25
xsel is a utility for interacting with the X windows copy buffers - in particular

```
xsel -bo
```

says "write the contents of the clipboard buffer (b) to standard output (o)" and

```
xsel -bi
```

says "read standard input (i) into the clipboard buffer (b)". In between, we pass the contents through iconv to turn the UTF-8 to ASCII. So now we (hopefully) have ASCII text in the clipboard buffer: the final piece is to fake a regular ctrl-v key combination to paste the result into the current window, which we can do with xdotool.

Neither xsel nor xdotool are installed by default so you will need to install them first either from your favorite package manager or via commandline using

```
sudo apt-get install xsel xdotool
```

The 
```

sh -c '... whatever ...'

```

part is just to assemble it all into a single command (you can think of it kind of like an 'inline' shell script).

Hope this helps. 

NB I haven't checked to see what happens if the clipboard doesn't contain text, or contains text that can't be transliterated to ASCII - and I haven't checked what happens if you try to use the shortcut in other applications. Treat it as experimental and use at your own risk!

---

