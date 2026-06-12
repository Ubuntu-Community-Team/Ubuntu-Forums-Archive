---
title: "Change title of emacs window?"
date: 2010-07-13
forum: Programming Talk
---

### Post by Zorgoth on 2010-07-13
I would really like it if the title of my emacs windows were something like "emacs - [buffer name]" rather than "emacs23@[computer-name];" when I have lots of emacs windows I would like to be able to find the one I want just by hovering my mouse; window previews helps a little but titles would definitely be ideal, particularly since window previews don't seem to work on minimized windows.

So how would I do that?  Is there any easy way?

---

### Post by johnl on 2010-07-13
Add the following to your .emacs file in your home directory:

```

(setq frame-title-format
  '("emacs - " (buffer-file-name "%f"
    (dired-directory dired-directory "%b"))))

```

This will give you the title "emacs - /path/to/file" instead of "emacs@hostname".

---

### Post by sujoy on 2010-07-13
Well the OP's question has been already answered. However, its to be noted that emacs is not meant to be used like notepad, where you open a new emacs instance for every file that you edit. Instead just open all the files in one emacs instance (run emacs as server and use emacsclient if you will), and just switch between the open buffers.

---

### Post by Zorgoth on 2010-07-13
I am aware that you can switch between buffers, but when I am working on 5 or 10 source files I find it easier to run 2-4 emacs instances in different workspaces.  I only run one on an individual workspace, usually with several frames.

Also, the paths could get rather long, so is there a way to make that display just the end of the path?

---

### Post by jpkotta on 2010-07-14
> **Zorgoth said:**
> 
Also, the paths could get rather long, so is there a way to make that display just the end of the path?

filename-nondirectory works like basename.  

Here's my title, in case you're interested:
```

(setq-default frame-title-format
              '(:eval
                (format "%s@%s: %s %s"
                        (or (file-remote-p default-directory 'user)
                            user-real-login-name)
                        (or (file-remote-p default-directory 'host)
                            system-name)
                        (buffer-name)
                        (cond 
                         (buffer-file-truename
                          (concat "(" buffer-file-truename ")"))
                         (dired-directory
                          (concat "{" dired-directory "}"))
                         (t
                          "[no file]")))))

```

---

### Post by johnl on 2010-07-14
> **jpkotta said:**
> filename-nondirectory works like basename.  

Here's my title, in case you're interested:


Awesome, thanks for sharing :)

---

### Post by nmaster on 2010-07-14
> **sujoy said:**
> Well the OP's question has been already answered. However, its to be noted that emacs is not meant to be used like notepad, where you open a new emacs instance for every file that you edit. Instead just open all the files in one emacs instance (run emacs as server and use emacsclient if you will), and just switch between the open buffers.
+1.  moreover there is no reason to even open emacs through a GUI.  the benefit of a text-editor like emacs is that you don't have to use a mouse.  that makes everything faster.

> **Zorgoth said:**
> I am aware that you can switch between buffers, but when I am working on 5 or 10 source files I find it easier to run 2-4 emacs instances in different workspaces. 

why not split the terminal? i sometimes like to full screen my terminal and then split emacs 4 ways. 

if you aren't familiar with emacs hot-keys and you like using a GUI, you might as well stick with gedit.  it gives you tabs and IIRC it titles the windows the way you want as well.

---

### Post by Zorgoth on 2010-07-14
I do split and full-screen the terminal.  Usually two or three frames, my preferred layout being a matlab shell in the upper left hand corner, the main script I'm working on in the lower half, and some other relevant script in the upper right hand corner, but often I am working with an awful lot of scripts; also, matlab-emacs seems to only like having one shell per instance of emacs, so when I want two (for example, one to do tests while one is busy) I need multiple instances.

Incidentally, Ctrl-Alt-Left and Ctrl-Alt-Right are also keyboard shortcuts; hence they allow very fast switches between different emacs instances so you can edit multiple sets of files concurrently.

(and speaking of running emacs in terminals, I run them in tty1-6 a lot to stop programs from popping up with annoying GUIs) - and there is a reason to run emacs in GUI mode - you get more keyboard shortcuts (and LaTeX previews work properly).

And yes, I do almost everything in emacs with the keyboard.  But sometimes it is faster to click an icon with a names on in in cairo-dock than sift through my workspaces.

By the way, I am currently having upgrading 32-bit to 64-bit encrypted Ubuntu woes.  When they are over I will try jpkotta's title.

---

### Post by Zorgoth on 2010-07-15
Just would like to mention that finally I had a chance to try your title and I am keeping it!  It's perfect!

---

