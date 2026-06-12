---
title: "miniHowTo: spell checking with nano including languages other than US English"
date: 2011-01-16
forum: Outdated Tutorials &amp; Tips
---

### Post by keithpeter on 2011-01-16
**miniHowTo: spell checking with nano including languages other than US English**

*This is my first howto so feedback on form as well as content welcome.*

The steps in this tutorial have been tested on Ubuntu 10.10 and Ubuntu 10.04. 

Nano is a simple command line editor that is installed on many Linux distributions including Ubuntu. Nano uses combinations of the control key (ctrl) and a letter to invoke commands, and the help bar and help files use the ^ character to represent the ctrl key. The command ^T will run a spell check on all the words in the current file and ask you to change or confirm the spelling of each word that does not appear in the spelling dictionary. Nano expects to find the spell command installed, and nano invokes this command without arguments or options.

Ubuntu does not have the spell command installed by default. When you install the spell command, the only dictionary installed initially is the US English one. The instructions below will show you how to

[LIST=1]
[*]Install the spell command
[*]Install additional dictionaries
[*]Set a global option to set the spell checking language
[*]Test spell checking in nano
[/LIST]

**1. Install the spell command**

Type the following command

```
sudo apt-get install spell
```

Apt will install the ispell program that provides the spell command, but will only install the US English dictionary by default.

If you use US English, you don't need the next two sections, just jump to section 4 to see how to test nano's spell check

**2. Install additional dictionaries**

There is a complete list of dictionaries available in the Ubuntu repositories on the [page that describes the Ubuntu ispell package]("http://packages.ubuntu.com/dapper/ispell-dictionary"). I installed the ibritish dictionary by typing the following command

```
sudo apt-get install ibritish
```

**3. Set the global language option**

Type the following

```
sudo select-default-ispell
```

You will see a 'dos' style selection box listing all the ispell dictionaries available on your system. Within the 'dos style' box

[LIST=1]
[*]Click the down arrow so that the dictionary you want is highlighted
[*]Press TAB to activate the OK button (it changes colour)
[*]Press Enter
[*]The 'dos style' box should disappear leaving you with your command prompt
[/LIST]

**4. Test in nano**

Start nano in a terminal window by typing 

```
nano sometextfile
```

Add some deliberate spelling errors to your file, and invoke the spell checker using ^T

The text cursor will jump to the first spelling error or word that is not in the dictionary. The nano window will look like the attached image. As you can see, you can edit the word and then change all instances of the word or just the current one. You can also choose not to change the word at all. When you have changed the word and pressed enter or issued the ^C command, nano jumps to the next word not in the spelling dictionary. When all the mis-spelled words have been corrected or ignored, nano says [finished checking spelling] at the bottom of the window.

Nano does *not* make spelling suggestions.

**Sources of information**

[http://www.ghacks.net/2010/12/10/add-spell-check-to-nano/](http://www.ghacks.net/2010/12/10/add-spell-check-to-nano/)
[http://packages.ubuntu.com/dapper/ispell-dictionary](http://packages.ubuntu.com/dapper/ispell-dictionary)
[http://www.matthew.ath.cx/cgi-bin/man/man2html?select-default-ispell+8](http://www.matthew.ath.cx/cgi-bin/man/man2html?select-default-ispell+8)

---

### Post by casbahdk on 2011-01-18
Great tutorial keithpeter, thank you, thank you, thank you! Any idea how to switch between languages without changing the default spell checking language every time you write something in another language?

---

### Post by keithpeter on 2011-01-18
> **casbahdk said:**
> Any idea how to switch between languages without changing the default spell checking language every time you write something in another language?

Thanks for the feedback casbahdk.

Alas, I don't know how to change the spell check language on the fly from within nano. 

It looks like nano can only issue the spell command without any arguments and then capture the output. You can call nano with an option (-s) to use a different spelling program (perhaps a script file that calls spell with a given language dictionary, something like spell-british.sh), however I don't think that is interactive, I think it just starts another session for the spellchecker.

I'll do some more googling and playing at the weekend. I have a job interview on Thursday.:roll:

---

### Post by maxter on 2011-02-09
another (better IMHO) choice is aspell, that have some other advantages on spell, like spelling suggestions

install aspell with:

```
sudo apt-get install aspell 
```

if you use a locale other than english, install the corresponding dictionary. i use italian so for me it was:

```
sudo apt-get install aspell-it
```

Now you must edit the file /etc/nanorc

```
sudo nano /etc/nanorc
```

you must find the following row and decomment it:

```
#set speller "aspell -x -c"
```              &#711;
```
set speller "aspell -x -c"
```

save and quit nano.

hitting ^t (ctrl+t) will now launch aspell.

---

### Post by casbahdk on 2011-02-09
Is it possible to switch between aspell dictionaries in nano?

---

