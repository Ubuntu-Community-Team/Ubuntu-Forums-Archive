---
title: "Virtual Terminals - tiny font size"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by kenworth on 2008-05-21
I use the virtual terminals for lots of tasks and to run some applications that use character mode. After an almost faultless upgrade to Hardy, I had to follow some guides to get back my 1024x764 on my desktop. I finally achieved this after trying lots of suggestions by installing ATI proprietory drivers (the guides were long and quite complicated for a noob like me).

The result is I now have a great desktop but tiny font on my virtual consoles (tty1-tty6) that display 128 char x 47 lines by instead of the usual 80 x 24.

I have tried dpkg-reconfigure console-setup and tried both the 'fixed' and 'vga' choices but it doesn't seem to change anything. I have searched for a meaningful HOWTO without success.

Any suggestions would be much appreciated.

---

### Post by unutbu on 2008-05-21
The command
```

consolechars -f Uni3-Terminus16.psf
```

will change your font to one called Uni3-Terminus16.psf. The `consolechars` command only works on virtual terminals; it won't work in X.

The command
```
locate Uni3-Terminus16
```
will show you the directory in which this font is located (probably /usr/share/consolefonts). You can look in there for other font options.

---

### Post by kenworth on 2008-05-21
Thanks unutbu, tried that but font is still small (i.e. 16) There are a few bigger ones in the folder (i.e. Uni3-Terminus20x10.psf but consolechars display error message
read_simple_font(): Bad font file format

---

### Post by unutbu on 2008-05-21
Hm. Yes, I get an error too (though a little different):
```

% consolechars -f Uni3-Terminus20x10
Cannot (yet) load a non-seekable RAW file
read_simple_font(): Invalid argument

% consolechars -f Uni3-Terminus20x10.psf
Cannot (yet) load a non-seekable RAW file
read_simple_font(): Invalid argument

% consolechars -f Uni3-Terminus20x10.psf.gz
Cannot (yet) load a non-seekable RAW file
read_simple_font(): Invalid argument

```

The only other thing I can think of is to change your virtual terminal resolution. I tried doing this on my own computer so I could give you good directions, but failed. I'll pass on what I did anyway; maybe you can make it work for you:

Reboot the machine. 
Wait for the 3 second GRUB countdown. 
Press ESC to get to the GRUB menu.
Press 'e' to edit the default boot stanza.
Use the down arrow key to highlight the kernel line
Press 'e' to edit the kernel line
Press End to go to the end of the line,
Type vga=ask to add that boot option.
Press 'b' to boot

You should be shown a list of resolutions. Type in the number corresponding to the resolution you desire. I didn't know if I was supposed to type the integer number (0--6?) or the hexadecimal, so I ended up trying each (no joy either time). It briefly gave me the resolution that I wanted, and then the machine abruptly decided to do a reboot.

So, I don't know the exact solution, but I hope this might lead you in the right direction. Googling "resolution virtual terminal" will come up with pages with similar directions, as well as some bug reports that changing virtual terminal resolution does not work under Gutsy (which is what I'm using). Maybe the problem is fixed under Hardy?

If you try what I did and it does not work, and you want to pursue this further, you might want to consider following the directions at [https://help.ubuntu.com/community/ConsoleFramebuffer](https://help.ubuntu.com/community/ConsoleFramebuffer).

My main hesitation with pointing you to this page immediately is that I don't understand the error message that they refer to in the introduction. The rest of the guide however seems to be a complicated workaround for changing virtual terminal resolutions.

---

### Post by kenworth on 2008-05-22
thanks unutbu, that is a good workaround.

---

### Post by unutbu on 2008-05-22
Oh great! I'm glad it worked out for you.

---

### Post by billyswong on 2010-04-28
> **kenworth said:**
> Thanks unutbu, tried that but font is still small (i.e. 16) There are a few bigger ones in the folder (i.e. Uni3-Terminus20x10.psf but consolechars display error message
read_simple_font(): Bad font file format

(Although it's an 2-years-old post but still) I faced a similar problem in Ubuntu 9.10 and found that although ``consolechars'' does not work, ``setfont'' do. The command ``setfont Uni3-Terminus20x10.psf'' works with no problem.

---

