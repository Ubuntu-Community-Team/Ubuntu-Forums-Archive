---
title: "how can I open a rails project in gmate?"
date: 2012-12-16
forum: Packaging and Compiling Programs
---

### Post by alonsh on 2012-12-16
I installed vmware in order to get a Linux system.

I started a project and created a database.

In addition, I wrote these lines in the Ubuntu, in order to get something like textmate (it is called: gmate):

sudo apt-add-repository ppa:ubuntu-on-rails/ppa
sudo apt-get update
sudo apt-get install gedit-gmate

I am searching how can I open a rails project in gmate, and didn't find (in textmate is: ett).

Can someone help me please?

---

### Post by gnusci on 2012-12-16
Maybe you should give more details, check this link:

[http://runningwithrails.com/2011/02/configuring-gedit-for-rails/](http://runningwithrails.com/2011/02/configuring-gedit-for-rails/)

---

### Post by alonsh on 2012-12-17
thank you, but where can I find: "Edit > Preferences > Plugins."

I pressed 'edit' and then: 'preferences'.
and I don't see 'plugins'.

this is my window (I can connect my username if it's needed):

[IMG]http://imageshack.us/scaled/landing/26/58861723.jpg[/IMG]

thanks!

---

### Post by Crimbo on 2013-03-06
> **alonsh said:**
> I don't see 'plugins'.

It's because Gmate is version 3 and the plugins were for version 2 apparently, so they do not show.

I am trawling the web to find a solution.

---

### Post by Crimbo on 2013-03-06
This might help... scroll to the bottom (You might find the document itself it pretty useful).

[https://gist.github.com/RaVbaker/2967695](https://gist.github.com/RaVbaker/2967695)

I think the plugins are a thing of the past now :(

None of these plugins are with the Gmate install...


[LIST]
[*]Snippets
[*]Code Comment
[*]Embedded Terminal
[*]Find in Files
[*]Rails Extract Partial
[*]Rails File Loader
[*]Session Saver (Optional)
[*]Smart Indent (Optional)
[*]Tab Switch (Optional)
[*]TextMate Style AutoCompletion
[/LIST]

source: [http://runningwithrails.com/2011/02/configuring-gedit-for-rails/](http://runningwithrails.com/2011/02/configuring-gedit-for-rails/)

---

### Post by Crimbo on 2013-03-06
Tips:

[LIST]
[*]Click 'View > Side Panel'
[*]Click 'Edit > Preferences: View; Display line numbers'
[*]Click 'Edit > Preferences: View; Display right margin at column; 100 fits best for Rails' (80 is the IBM punch card standard)
[*]Click 'Edit > Preferences: Editor; Enable automatic indentation'
[/LIST]

[LIST]
[*]Gmate has added to the Font & Colours list:
[LIST]
[*]Edit > Preferences: Font & Colours
[*]Choose 'Railscasts' for authenticity
[*]Untick 'Use the system fixed width font' - In other words, use 'Monospace'.
[/LIST]
[/LIST]


I was wrong, few of the previous plugins have been updated to Gmate v.3 and are installed automatically when you install Gmate. Look through the plugins, as there is a Rails File Loader one.

Here's the current v.3 plugins...
[https://github.com/gmate/gmate/tree/master/plugins/gedit3](https://github.com/gmate/gmate/tree/master/plugins/gedit3)

These might be handy for setting up a rails environment in Gedit... but entries are old...
[http://rbjl.net/22-rubybuntu-4-make-gedit-better-than-any-ide](http://rbjl.net/22-rubybuntu-4-make-gedit-better-than-any-ide)
[http://rbjl.net/23-gedit-external-tools-ruby-helpers-git-integration-and-more](http://rbjl.net/23-gedit-external-tools-ruby-helpers-git-integration-and-more)

These are where the tools go...[COLOR=#000000][FONT=sans-serif][/FONT][/COLOR][COLOR=#000000][FONT=sans-serif][/FONT][/COLOR][COLOR=#000000][FONT=sans-serif][TABLE]
[TR]
[TD][/TD]
[TD]System tools path
[/TD]
[TD]User tools path
[/TD]
[/TR]
[TR]
[TD]gedit 2
[/TD]
[TD]$XDG_DATA_DIRS/gedit-2/plugins/tools
[/TD]
[TD]~/.gnome2/gedit/tools
[/TD]
[/TR]
[TR]
[TD]gedit 3
[/TD]
[TD]/usr/share/gedit/plugins/externaltools/tools
[/TD]
[TD]~/.config/gedit/tools
[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
source: [https://live.gnome.org/Gedit/Plugins/ExternalTools](https://live.gnome.org/Gedit/Plugins/ExternalTools)

---

### Post by peng6662001 on 2013-03-12
bump

---

### Post by Crimbo on 2013-03-12
> **alonsh said:**
> 
I pressed 'edit' and then: 'preferences'.
and I don't see 'plugins'.


I've just thought... did you open Gmate after signing into Ubuntu?

type...
gmate
...at the command prompt.

Looking at your screenshot, I think you are looking at the wrong preferences window.

---

