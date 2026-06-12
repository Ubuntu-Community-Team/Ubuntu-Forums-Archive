---
title: "vim background color in a shell"
date: 2009-05-23
forum: Programming Talk
---

### Post by mustang on 2009-05-23
Hi all,

one of my summer goals is to learn vim so I'm diving head first.

I have to do my programming remotely in a shell. I know how to install color themes but for some reason, the background color never changes. When I do ":colorscheme desert", the syntax highlighting is in effect but the background color does not change to the dark gray it is supposed to. Rather, it stays the default color of my terminal. 

This does not happen in gVim---the background colors changes correctly. However, gVim is not an option for me since I have to use vim in a shell.

Any ideas?

Thank you,

Manish

---

### Post by SadaraX on 2009-05-23
What sort of console/terminal emulator program are you using? Gnome-terminal? Konsole? Xterm? Aterm? Other?

You mention remote program. First, I'm familiar with that. :) Done it a lot. Second, are you encountering the color issue on the remote machine? On your local machine? Or both?

---

### Post by hessiess on 2009-05-23
As far as I can work out, it is only possabe to change the background colour in the GUI version, the CLI version always uses the terminal background colour.

---

### Post by SadaraX on 2009-05-23
> **hessiess said:**
> As far as I can work out, it is only possabe to change the background colour in the GUI version, the CLI version always uses the terminal background colour.

I usually don't even think about changing the background color, since I frequently have my console set to be transparent. However, I opened a new konsole here, and tested it by doing :colorscheme blue

Attached is an image of what it looks like. So, obviously it can change the background color in my terminal. There must be something more going on your end. Have you customized your .vimrc file? Perhaps there is a conflict there.

---

### Post by mustang on 2009-05-23
> **SadaraX said:**
> What sort of console/terminal emulator program are you using? Gnome-terminal? Konsole? Xterm? Aterm? Other?

You mention remote program. First, I'm familiar with that. :) Done it a lot. Second, are you encountering the color issue on the remote machine? On your local machine? Or both?

Hi SadaraX,

I'm using gnome-terminal on my end. I'm encountering the issue on the remote machine.

> I usually don't even think about changing the background color, since I frequently have my console set to be transparent. However, I opened a new konsole here, and tested it by doing :colorscheme blue

Attached is an image of what it looks like. So, obviously it can change the background color in my terminal. There must be something more going on your end. Have you customized your .vimrc file? Perhaps there is a conflict there.

Hmmm that's weird. Doing ":colorscheme blue" works fine. But when I do ":colorscheme desert", it reverts back to the default terminal background color. My .vimrc is empty.

---

### Post by SadaraX on 2009-05-23
I tested desert on my computer here. The background color does not change but the foreground colors do change. Of course, there is a possibility that the desert background is already the same color as my shell colors...

---

### Post by mustang on 2009-05-24
> **SadaraX said:**
> I tested desert on my computer here. The background color does not change but the foreground colors do change. Of course, there is a possibility that the desert background is already the same color as my shell colors...

The desert theme is a really dark blue.

---

### Post by stroyan on 2009-05-24
The default behavior for vim usually results in an assumption that the terminal only handles 8 basic colors.
Many terminal emulators such as gnome-terminal can actually handle more colors.
Telling vim about that will allow it to set background colors that more closely match the color schemes instead of substituting blue, black, or white.

Add this to your .vimrc-
set t_Co=256

You can get a similar effect by setting the TERM environment variable to TERM=xterm-256color .

---

### Post by mustang on 2009-05-24
> **stroyan said:**
> The default behavior for vim usually results in an assumption that the terminal only handles 8 basic colors.
Many terminal emulators such as gnome-terminal can actually handle more colors.
Telling vim about that will allow it to set background colors that more closely match the color schemes instead of substituting blue, black, or white.

Add this to your .vimrc-
set t_Co=256

You can get a similar effect by setting the TERM environment variable to TERM=xterm-256color .

Hi stroyan,

that works with my local terminal. It does not work when I'm logged into a shell.

---

### Post by ibuclaw on 2009-05-24
For when in a terminal (vim)
```
:hi Normal ctermbg=white
```
You need a colour term though for it to work. (Most terminals are colour terms)

Look up
```
:help hi
```
For more info ;)

---

### Post by SadaraX on 2009-05-24
> **mustang said:**
> Hi stroyan,

that works with my local terminal. It does not work when I'm logged into a shell.

First, does the vim on the remote machine support full colors? Also, did you change your .vimrc on the remote machine as well?

---

