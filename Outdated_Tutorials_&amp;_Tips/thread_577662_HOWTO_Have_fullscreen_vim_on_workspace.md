---
title: "HOWTO: Have fullscreen vim on workspace"
date: 2007-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by mhueting on 2007-10-16
After loads of trying and figuring out, I found a sort of workaround to be able to have a fullscreen gVim on my second workspace. Now I have firefox running in my 1st and vim on my second. This is my first tutorial, so bear with me, and tell me what I could improve ;)

**Why?**
Because it looks damn cool, that's why.

**Tutorial**

1a. Install devilspie/make sure that it is installed:

```
sudo apt-get install devilspie
```

1b. Install xsendkeys/make sure that it is installed:

```
sudo apt-get install xsendkeys
```

2. Make a devilspie config directory in your home dir:

```
mkdir ~/.devilspie
```

3. Make a file (with Vim ;) ) inside this dir:

```
vim ~/.devilspie/vim.ds
```

In this file, past this:

```

(if (is (application_name) "Vim") (begin (set_workspace 2) (undecorate) (maximize) ) ) 

```

Save it and exit

4. Make a bashscript in your home directory, or in /usr/local/bin, or wherever you want:

```
vim ~/vimfull
```

and paste this:

```

devilspie &
gvim
xsendkeys "Control_L+Alt_L+Right"
xsendkeys "Control_L+Alt_L+Left"
xsendkeys "Control_L+Alt_L+Right"
xsendkeys "Control_L+Alt_L+Left"
killall gnome-panel
killall devilspie

```

5. Make it executable:

```
chmod a+x ~/vimfull
```

6. Execute:

```

cd ~
./vimfull

```

7. Voila! If you switch to your second desktop, you'll see that there now is a fullscreen Vim running. It's kind of a hack, because when you kill gnome-panel, it will restart automatically. When there is an undecorated version of vim running maximized in the second workspace, the gnome-panel will start underneath Vim, and you have a completely maximized Vim (please, do notice, I'm kind of a linux noob, so I don't know completely if this is how it works, but anyway, it works, so I'm not complaining :biggrin:

I don't know if this would also work with other applications, but I'm not going to test that. I have now Vim running completely fullscreen in my second workspace without the gnome-panel and with guioptions set to not show the menubar or toolbar. So it looks REALLY kickass.

---

### Post by boob11 on 2007-11-22
thnx

---

### Post by hugmenot on 2007-11-22
Do you mind if I gave you a one-liner (GUI) solution for this? Would that be a turn-off?

---

### Post by sol0 on 2007-12-02
the principle behind this is working fine also with virtualbox:

(if (is (application_name) "VBoxManage startvm mybox ") (begin 
(set_workspace 2) (undecorate) 
(maximize) ) )

devilspie &
VBoxManage startvm mybox
xsendkeys "Control_L+Alt_L+Right"
killall gnome-panel
killall devilspie

but it could be adjusted more if you are more technical, also some problems with compiz-fusion...

---

### Post by hugmenot on 2007-12-02
Ok, you can define a full-screen shortcut in the Gnome "Keyboard Shortcuts" panel. This shortcut works for all apps. I have it set to Mod3+F11 and it makes Gvim fullscreen without any additional hacking.

---

### Post by tomauty on 2007-12-02
A screenshot or two would be nice. For tutorials after this one if you don't feel like making one for this.

---

