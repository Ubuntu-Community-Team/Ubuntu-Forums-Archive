---
title: "Spell checker?"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by Yezinki on 2013-01-10
Despite trying every thing, enabling google spell checker it won't underline an incorrect word. I that normal or only happening with my G Chrome browser?

Thanks.

---

### Post by TheFu on 2013-01-10
There are lots of spell checkers for Linux.  
* aspell
* ispell
and one of the first exercises that someone learns when starting out in shell programming, is how to make a spell checker using simple UNIX CLI commands.

I know that Firefox has a spell checker too, but there is a toggle to disable it AND some websites seem to disable it automatically. I think those usually have lots and lots of javascript.  The firefox spell checker does work here.  I'm seeing lots of non-standard words underlined above. ;)

Sorry, I don't know anything about chrome.  Perhaps leading with "chromium spellcheck" as the title would help?

---

### Post by Yezinki on 2013-01-10
Thanks TheFu for your reply.

How does one install * aspell, * ispell & would they work with Google Chrome?

---

### Post by TheFu on 2013-01-10
Both are probably already installed. They are CLI spell checkers, so any program that allows you to customize external program calls and return the output should work.

* Open a terminal.
* Type "**aspell**" to see a quick usage/help screen.
Usually you want a text file to pass as an argument. **aspell check some_text_file**
To learn more, read the man page.  **man aspell**

I'm always confused when people choose to use chrome over chromium and don't work for google. Why?

---

### Post by Impavidus on 2013-01-10
```
sudo apt-get install aspell
sudo apt-get install ispell
```In other words, install the package. They may be installed by default. Make sure you have the dictionaries for your favorite languages installed too. These packages are named [FONT=Courier New]aspell-**[/FONT] (substitute for your language) and [FONT=Courier New]i****[/FONT] (again, substitute your language).

In case your language has a rich morphology (hungarian, estonian, euskara) you may want hunspell.

---

### Post by Yezinki on 2013-01-10
```
sudo apt-get install aspell
sudo apt-get install ispell
```

Using this shall install languages, I only need English US, so what else do I need to do?

How does one install dictionaries?

After all this shall google spell checker work?

Thanks.

---

### Post by Yezinki on 2013-01-10
TheFu I have same issues with both Chromium & G Chrome.

```
vaio@VGC-LS1:~$ aspell
Usage: aspell [options] <command>
<command> is one of:
  -?|usage         display a brief usage message
  help             display a detailed help message
  -c|check <file>  to check a file
  -a|pipe          "ispell -a" compatibility mode
  [dump] config    dumps the current configuration to stdout
  config <key>     prints the current value of an option
  [dump] dicts | filters | modes
    lists available dictionaries / filters / filter modes
[options] is any of the following:
  --encoding=<str>            encoding to expect data to be in
  --mode=<str>                filter mode
  -l,--lang=<str>             language code
  -d,--master=<str>           base name of the main dictionary to use
  --sug-mode=<str>            suggestion mode
vaio@VGC-LS1:~$ 

```

---

### Post by Impavidus on 2013-01-10
For ispell install iamerican, iamerican-small, iamerican-large, iamerican-huge and/or iamerican-insane, depending on the size of dictionary you want. A larger dictionary will give you less false positives, but will at the same time accept wrongly spelled words that happen to be spelled the same as uncommon words.

For aspell use aspell-en.

Considering integration in your browser: Maybe the browser checks automatically for the presence of a spell checker on your system, else I don't know how to configure it. I'm sure it must be possible though.

Funny, I just saw that aspell for dutch gives me way more false positives than genuine errors. It fails on almost every compound.

---

### Post by Yezinki on 2013-01-10
Thanks Impavidus.

---

### Post by orb9220 on 2013-01-17
Don't know if relevant? As my ubuntu distro was french based.
about:config and search spellchecker.dictionary
mine was set to Fr changed to en-US and all is well again.

---

