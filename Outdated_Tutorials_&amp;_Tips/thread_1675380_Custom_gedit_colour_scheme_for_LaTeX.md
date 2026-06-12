---
title: "Custom gedit colour scheme for LaTeX"
date: 2011-01-25
forum: Outdated Tutorials &amp; Tips
---

### Post by chandra on 2011-01-25
I recently made the switch from Kubuntu 10.04 to Ubuntu 10.10 to enjoy the greater polish and stability of the latter distribution. Among the applications that I had used a lot in Kubuntu was Kile, the customized editor for TeX/LaTeX and friends.

Despite its many features, Kile was of late auto-deleting text that had been highlighted by a left mouse click, and I was losing text in my documents without being aware of it. This was one among several reasons I made the switch to Ubuntu.

It was a pleasure to find out that gedit was feature-rich and stable; so the only question was whether it could match at least the major features of Kile. This writeup describes how I went about customizing gedit so that it performed well enough for me not to miss Kile any more in Ubuntu.

Here is what I did:

1. ```
sudo apt-get install gedit-latex-plugin
```

This plugin made available in gedit many of the features that I had grown to depend on in Kile: a document outline with LaTeX section and sub-section headings, a symbol inserter for mathematical symbols, commands for italics, bold, and other font-styles, to name just three. The plugin may be activated via

Edit -> Preferences -> Plugins

by ticking the appropriate checkbox.

2. Text-highlighting was already available through the gedit colour schemes bundled with gedit, along with the default latex.lang file, also installed as standard. These were good, but I needed some customized LaTeX syntax highlighting, preferably using some of the colour-rich schemes available for use with vim. For this I needed to (a) download the vim colour scheme and (b) a script for converting the vim scheme into one that could be used by gedit.

3. Download a vim scheme that you like. I found Zenburn to be suited for my taste and use. Using a web browser, I downloaded it from

[http://www.vim.org/scripts/script.php?script_id=415](http://www.vim.org/scripts/script.php?script_id=415)

The extracted file is named zenburn.vim

4. Download the script vim2gtksourceview.py to translate vim colour schemes into a gtksourceview2-compatible XML file from

[http://vim2gtksourceview2.googlecode.com/files/vim2gtksourceview2-0.2.2.tar.gz](http://vim2gtksourceview2.googlecode.com/files/vim2gtksourceview2-0.2.2.tar.gz)

using a web browser or

```
wget http://vim2gtksourceview2.googlecode.com/files/vim2gtksourceview2-0.2.2.tar.gz
```

Unpack the archive with

```
tar -zxvf vim2gtksourceview2-0.2.2.tar.gz
```

or using your favourite archiving application, and go into the directory vim2gtksourceview2 to access the executable Python script vim2gtksourceview.py

5. Put the zenburn.vim file in the same directory as the Python script and generate the file zenburn.xml in the same directory so:

```
./vim2gtksourceview.py < zenburn.vim > zenburn.xml
```

Of course if you are familiar with directories and paths, you may store all your .vim files in one directory and all your gtksourceview2-compatible .xml files in another, and write a small bash script to automate the translation of all vim colour schemes.

6. I needed to highlight brackets [] and braces {} and their contents in LaTeX. The file 

/usr/share/gtksourceview-2.0/language-specs/latex.lang

lacked the schema to do this. I copied and amended the file and saved it as

~/.local/share/gtksourceview-2.0/language-specs/latex.lang

creating any necessary parent directories along the way. This keeps the system latex.lang file intact but personalizes the amendments for the user in question.

7. If you wish to understand the gtksourceview2 lang syntax so that you may make modifications to suit yourself, take a look at this tutorial

[http://library.gnome.org/devel/gtksourceview/stable/lang-tutorial.html](http://library.gnome.org/devel/gtksourceview/stable/lang-tutorial.html)

and this reference

[http://library.gnome.org/devel/gtksourceview/stable/lang-reference.html](http://library.gnome.org/devel/gtksourceview/stable/lang-reference.html)

8. I then modified the translated zenburn.xml file with the extra lines for LaTeX syntax highlighting, including the custom bracket highlighting mentioned above, using the gedit Kate colour scheme file

/usr/share/gtksourceview-2.0/styles/kate.xml

as a guide.

9. I saved the modified zenburn.xml file as

~/.gnome2/gedit/styles/g-zenburn.xml

10. I found that the parentheses highlighting interfered with the highlighting of bibtex files. Moreover I needed to highlight "url" as a keyword in bibtex files. Accordingly, the bibtex.lang and latex.lang files were modified as well as g-zenburn.xml to accommodate these changes. All three files may be downloaded from the links below.

11. Finally, I invoked the g-zenburn colour scheme via

Edit -> Preferences -> Font & Colors -> Color Scheme -> Add

12. The amended bibtex.lang, latex.lang and the g-zenburn.xml files may be downloaded from

[url]http://academy.swanlotus.com/downloads/latex.lang[/url

][http://academy.swanlotus.com/downloads/bibtex.lang](http://academy.swanlotus.com/downloads/bibtex.lang)

and

[http://academy.swanlotus.com/downloads/g-zenburn.xml](http://academy.swanlotus.com/downloads/g-zenburn.xml)

using a web browser or

```
wget http://academy.swanlotus.com/downloads/latex.lang
wget http://academy.swanlotus.com/downloads/bibtex.lang
wget http://academy.swanlotus.com/downloads/g-zenburn.xml
```

The above chronicles what I did in the hope that it might help someone else to customize their favourite colour scheme for their favourite language to work with gedit. The vim colour scheme, the .lang file, and the syntax highlighting used in the .xml file, are all customizable according to your need and taste.

Enjoy!

---

### Post by 0ptix on 2011-02-28
Nice! thanks a lot for that. it made quite a difference to my latex editing experience and is much appreciated. :)

---

### Post by waxmati on 2011-03-03
Thanks a lot. I was just switching from Kile to gedit too and was just getting mad at no bracket-highlighting...

---

### Post by Cenoforums on 2011-04-18
Thank you so much for this! Unfortunately, it did not work as expect with the [mustang colorscheme]("http://hcalves.deviantart.com/art/Mustang-Vim-Colorscheme-98974484?offset=30"). The produced colorscheme only had the background, text and basic highlight. all highlights were of the same color.

---

### Post by chandra on 2011-04-23
> **Cenoforums said:**
> Thank you so much for this! Unfortunately, it did not work as expect with the [mustang colorscheme]("http://hcalves.deviantart.com/art/Mustang-Vim-Colorscheme-98974484?offset=30"). The produced colorscheme only had the background, text and basic highlight. all highlights were of the same color.

Cenoforums, I get three colours apart from text and comment highlighting: yellow for commands, green for mathematics, and orange for stuff in brackets. I did not look at .bib files.

Insert the stuff below *before* the closing ```
</style-scheme>
``` in your Mustang_Vim_Colorscheme_by_hcalves.xml file.

```
<!-- 

Modifications from Kate Scheme for LaTeX specific identifiers 
Inserted by Chandra Chandrasekhar on 24 Jan 2011

The parentheses highlighting requires a modified latex.lang file

-->
	
	<style name="latex:display-math"		use-style="def:boolean"/>
	<style name="latex:inline-math"			use-style="def:string"/>
	<style name="latex:math-bound"			use-style="def:string"/>
	<style name="latex:common-commands"		use-style="def:preprocessor"/>
	<style name="latex:command"				use-style="def:preprocessor"/>
	<style name="latex:parentheses"			use-style="def:number"/>
	<style name="latex:include"				use-style="latex:common-commands"/>
	<style name="latex:usepackage"			use-style="latex:common-commands"/>	
	
<!-- Added biblatex highlighting as well on 01 Feb 2011 -->
	
	<style name="bibtex:field"				use-style="def:identifier"/>
	<style name="bibtex:entry-type"			use-style="def:preprocessor"/>
```

Is your mileage better now?

HTH.

---

### Post by chandra on 2011-04-23
Cenoforums, I have taken a second look at the mustang theme and find that several entities share the same colours. A slightly more colourful scheme using the mustang colours is given below to be appended *before* the last xml closing tag of the file.

```
<!-- 

Modifications from Kate Scheme for LaTeX specific identifiers 
Inserted by Chandra Chandrasekhar on 24 Jan 2011

The parentheses highlighting requires a modified latex.lang file

-->
	
	<style name="latex:display-math"		use-style="def:boolean"/>
	<style name="latex:inline-math"			use-style="def:constant"/>
	<style name="latex:math-bound"			use-style="def:constant"/>
	<style name="latex:common-commands" use-style="def:number"/>
	<style name="latex:command"				use-style="def:preprocessor"/>
	<style name="latex:parentheses"			use-style="def:type"/>
	<style name="latex:include"				use-style="latex:common-commands"/>
	<style name="latex:usepackage"			use-style="latex:common-commands"/>	
	
<!-- Added biblatex highlighting as well on 01 Feb 2011 -->
	
	<style name="bibtex:field"				use-style="def:identifier"/>
	<style name="bibtex:entry-type"			use-style="def:preprocessor"/>
```

A more varied and colourful scheme than this will result if you decide to bold some of the colours but then you cannot invoke pre-defined highlighting as shown above. You need to define the appearance explicitly for each entity.

---

