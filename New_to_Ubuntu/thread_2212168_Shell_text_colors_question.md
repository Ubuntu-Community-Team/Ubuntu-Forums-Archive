---
title: "Shell text colors question"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by Priest Apostate on 2014-03-19
My shell is currently showing commented text in a dark blue color, which is difficult to see against a black shell background. Can someone point me out to the webpage that gives instructions on how to customize commented text colors in bash?

---

### Post by ajgreeny on 2014-03-19
I am sure it can be done, (don't know how), but I wonder if it might be easier and quicker to change the colour of your terminal background.

---

### Post by Priest Apostate on 2014-03-19
Where's the fun in that? :-)

---

### Post by ajgreeny on 2014-03-19
> **Priest Apostate said:**
> Where's the fun in that? :-)
Good point!
I'll keep watching this thread and I might learn something new.

---

### Post by steeldriver on 2014-03-19
With tput maybe?

[ATTACH=CONFIG]251301[/ATTACH]

See [http://linuxtidbits.wordpress.com/2008/08/11/output-color-on-bash-scripts/](http://linuxtidbits.wordpress.com/2008/08/11/output-color-on-bash-scripts/) for example

---

### Post by Hadaka on 2014-03-19
Here ya go...
[http://ubuntugenius.wordpress.com/2011/07/11/how-to-change-the-command-line-prompt-colour-in-the-ubuntulinux-terminal/](http://ubuntugenius.wordpress.com/2011/07/11/how-to-change-the-command-line-prompt-colour-in-the-ubuntulinux-terminal/)

---

### Post by vasa1 on 2014-03-19
> **Hadaka said:**
> Here ya go...
[http://ubuntugenius.wordpress.com/2011/07/11/how-to-change-the-command-line-prompt-colour-in-the-ubuntulinux-terminal/](http://ubuntugenius.wordpress.com/2011/07/11/how-to-change-the-command-line-prompt-colour-in-the-ubuntulinux-terminal/)
I think OP wants to do more than that.
This is what I used to change my terminal prompt color: [http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html).

As for the rest, I wonder what LS_COLORS are in the output of **env**:
```
[07:53 AM] ~ $ env
...
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
...
```
And if these are related to OP's question, how are they set and how can they be changed?

---

### Post by vasa1 on 2014-03-19
Oh, I also reread OP's question and the issue is "commented text". Unfortunately, OP hasn't specified the context. One assumes it's an editor like ... ? And each editor may have its own settings.

---

### Post by CharlesA on 2014-03-19
When I use VI with putty, the blue text is super dark, but you can change the colors in the Putty config.

The OP hasn't said how they are connecting or if they are just using a plain terminal.

---

### Post by vasa1 on 2014-03-19
> **CharlesA said:**
> ...
The OP hasn't said how they are connecting or if they are just using a plain terminal.
Could you please explain a bit more? Is the color scheme in an editor affected by the mode of connection or type of terminal?
What about just regular end users at home (not servers/admins/hackers) who want to use vi or emacs or nano?

---

### Post by CharlesA on 2014-03-20
> **vasa1 said:**
> Could you please explain a bit more? Is the color scheme in an editor affected by the mode of connection or type of terminal?
What about just regular end users at home (not servers/admins/hackers) who want to use vi or emacs or nano?

Depends on what terminal you use, I think. There should be a setting in xterm for the colors. Same in Konsole.

[http://askubuntu.com/questions/270711/how-can-i-change-the-default-color-for-all-the-text-in-the-system-manually](http://askubuntu.com/questions/270711/how-can-i-change-the-default-color-for-all-the-text-in-the-system-manually)

EDIT: If you use gnome-terminal, you can change what profile you use for your settings: Edit > Profiles... > Edit > Colors

---

### Post by vasa1 on 2014-03-20
> **CharlesA said:**
> Depends on what terminal you use, I think. There should be a setting in xterm for the colors. Same in Konsole.

[http://askubuntu.com/questions/270711/how-can-i-change-the-default-color-for-all-the-text-in-the-system-manually](http://askubuntu.com/questions/270711/how-can-i-change-the-default-color-for-all-the-text-in-the-system-manually)

EDIT: If you use gnome-terminal, you can change what profile you use for your settings: Edit > Profiles... > Edit > Colors

Let's see what OP's response is. BTW, your link led me to [http://askubuntu.com/questions/17299/what-do-the-different-colors-mean-in-the-terminal](http://askubuntu.com/questions/17299/what-do-the-different-colors-mean-in-the-terminal) which is also informative.

---

### Post by CharlesA on 2014-03-20
Oh cool. I don't think I have that enabled on my server or Fedora box. Thanks for the link!

---

### Post by Impavidus on 2014-03-20
> **CharlesA said:**
> When I use VI with putty, the blue text is super dark, but you can change the colors in the Putty config.

The OP hasn't said how they are connecting or if they are just using a plain terminal.
VIm makes the comments dark blue on a light background or light blue on a dark background. Sometimes it guesses the background wrong. This can be fixed with the setting (in VIm)```
:set background=light
:set background=dark
```

---

### Post by su:bhatta on 2014-03-20
I am a little confused by this , but does the OP want the Terminal to have font colors something like this : [http://irenegr.deviantart.com/art/Debian-sid-jessie-403134366](http://irenegr.deviantart.com/art/Debian-sid-jessie-403134366)

Irene is in this forum too, I have seen her screenshots in Cafe thread and really like her use of colors.

Am keeping a lookout on this thread to learn something new, same as ajgreeny. :)

---

### Post by Priest Apostate on 2014-03-20
I'm using PuTTY for accessing the server directly. It looks like I may be able to edit the color configurations from there. 
I am using Vi to do any type of editing - that is where I see the dark blue text. 

Currently looking up tput as well.

---

### Post by CharlesA on 2014-03-20
> **Priest Apostate said:**
> I'm using PuTTY for accessing the server directly. It looks like I may be able to edit the color configurations from there. 
I am using Vi to do any type of editing - that is where I see the dark blue text. 

Yeah, you can change the colors from Putty itself, so it would probably be easier than messing with the colors of the terminal.

See here:
[http://dag.wiee.rs/blog/content/improving-putty-settings-on-windows](http://dag.wiee.rs/blog/content/improving-putty-settings-on-windows)

---

### Post by steeldriver on 2014-03-20
I think Impavidus has the easiest solution

[ATTACH=CONFIG]251324[/ATTACH]

Then directly in vi (command mode)
```

:set background=dark

```

[ATTACH=CONFIG]251325[/ATTACH]

You could put it in your .vimrc file

---

