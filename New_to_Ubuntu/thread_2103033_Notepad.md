---
title: "Notepad?"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by Yezinki on 2013-01-09
What is the counterpart of notepad in Ubuntu?

Thanks.

---

### Post by jerome1232 on 2013-01-09
gedit

---

### Post by Pletched on 2013-01-09
leafpad because it has less features unlike gedit, and some what like notepad itself.

---

### Post by Yezinki on 2013-01-09
Thanks jerome1232.

---

### Post by Yezinki on 2013-01-09
What is leafpad? How do i install it?

Thanks.

---

### Post by Pletched on 2013-01-09
Thorough software centre.

And through terminal

```
sudo apt-get install leafpad
```

---

### Post by Yezinki on 2013-01-09
Thanks Pletched.

---

### Post by haqking on 2013-01-09
Gedit if running Gnome DE.

There is also nano, kate,  vi, vim, gvim, eclipse, emacs,  leafpad as mentioned.

it depends what DE you are using as to what the default one is you have installed.

Peace

---

### Post by slickymaster on 2013-01-09
Personally, I like and use a lot Geany, wich is available through the official Ubuntu archives (Universe section).
```
apt-get install geany
```
You might find newer versions in the Ubuntu Geany PPA at [https://launchpad.net/~geany-dev/+archive/ppa](https://launchpad.net/~geany-dev/+archive/ppa)

Like many others, Geany also has severall plugins available in the repositories. You ca install them via:
```
sudo apt-get install geany-plugins
```
or
```
sudo apt-get install geany-plugin-{pluginname}
```
To see the list of plugins available in the repositories use:
```
apt-cache search geany
```
Alternatively (GUI method), use Synaptic (System -> Administration -> Synaptic Package Manager) and search for "geany".
Note: you must have the "Universe" repository enabled.

---

### Post by Yezinki on 2013-01-11
Installed geany & it's plugins. But when I saved a document & reopened, it opened in gedit?

Thought it would be similar to notepad?

Any suggestions?

Thanks.

---

### Post by slickymaster on 2013-01-11
You have to make Geany your default text editor. You can do it either via command line:
```
sudo update-alternatives --config editor
```
or via a graphical alternative using Gnome Alternatives:
```
sudo apt-get install galternatives
```
Run GAlternatives, select editor in the left column, and then add/choose Geany on the right.

---

### Post by Bölvaður on 2013-01-11
Do not make Geany the default text editor. I use it extensively but I would still not use it instead of gedit.

Just use gedit, it is a lot more powerful than notepad but you should still feel at home with it.

---

### Post by Yezinki on 2013-01-11
Thanks, which should I choose?

```
vaio@VGC-LS1:~$ sudo update-alternatives --config editor
[sudo] password for vaio: 
There are 3 choices for the alternative editor (providing /usr/bin/editor).

  Selection    Path               Priority   Status
------------------------------------------------------------
* 0            /bin/nano           40        auto mode
  1            /bin/ed            -100       manual mode
  2            /bin/nano           40        manual mode
  3            /usr/bin/vim.tiny   10        manual mode

Press enter to keep the current choice[*], or type selection number: 

```

---

### Post by slickymaster on 2013-01-11
You really should focus on what is the aim you intend to use it for. If you primarily pretend to use to write code, then you should go with Geany or Vim. But if you'll just use it as a simple notebook, then probably nano should be your choice.

---

### Post by Yezinki on 2013-01-11
I use notepad to type text before posting on my Drupal CMS website. That's it only purpose.

---

### Post by slickymaster on 2013-01-11
Personally I never worked with the Drupal framework, so I'm probably not the best person to advise you, since I don't know what are the needs in terms of developing for that platform.

---

### Post by Yezinki on 2013-01-11
What commands do I use to unintsall geany & it's associated plugins?

Thanks.

---

### Post by bab1 on 2013-01-11
I think you should decide first if you want a terminal based editor (nano, ed, vim) or a GUI based editor (leafpad, gedit, gvim, etc).  You can leave them all installed and play with them.  I use vim for terminals and gedit for GUI.  I use BlueFish for HTML editing.

The point I'm making is you can use them all until you find the ones you want on either the terminal or GUI desktop.

---

### Post by Yezinki on 2013-01-11
Thanks for your sharing your expert views bab1.

How does one install BlueFish?

---

### Post by bab1 on 2013-01-11
> **Yezinki said:**
> Thanks for your sharing your expert views bab1.

How does one install BlueFish?

BlueFish should be in the repos so you can use USC or Synaptic to install or from the command line you can do this ```
sudo apt-get install bluefish
```
...If you want to remove a package you should do this```
sudo apt-get purge <package>
```
...where <package> is the name of the package you want to remove.

---

### Post by Zill on 2013-01-11
> **Yezinki said:**
> ...How does one install BlueFish?
See this guide...
[LIST]
[*][How does one install/uninstall apps in Ubuntu]("http://ubuntuforums.org/showthread.php?t=2064288")
[/LIST]

---

### Post by Yezinki on 2013-01-12
Thanks bab1 & Zill apprecaite your expert assistance.

---

