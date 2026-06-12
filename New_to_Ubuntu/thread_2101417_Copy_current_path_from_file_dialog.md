---
title: "Copy current path from file dialog"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by ygoe on 2013-01-04
In gedit, when opening a file, the path of the currently opened file is displayed in that dialog with some buttons, one for each level. But I want to copy the path as text so that I can save a new file in the same path, which is not preselected otherwise. I don't want to remember and type in the path every time, that's what the clipboard is for. But gedit won't let me copy that path. Any idea?

---

### Post by sudodus on 2013-01-04
Yes, when you select ***Save as*** the same directory will be preselected and shown. Or maybe I don't understand your problem?

Edit: And when you select ***Save*** (ctrl s) it defaults to writing to the same directory/filename.

---

### Post by ygoe on 2013-01-04
I have opened one file in /some/very/long/and/hard/to/reembemr/path. Then I create a new file with Ctrl+N. Last time I tried to save this file, my home folder or something equally useless was preselected. So I went back to the other file and went to the Open File dialog, where the file's current path is already selected - but no way to copy it into the clipboard.

Oh, and when I want to enter a path alone, to browse the files there and then select a new file name, I entered the path, hit the Enter key and boom - the dialog was closed and an error message told me that this was a directory. Yes I Know.

(I'm a Windows user. Please tell me what I need to do differently to get the same stuff done on Ubuntu/Gnome.)

---

### Post by sudodus on 2013-01-04
> **LonelyPixel said:**
> I have opened one file in /some/very/long/and/hard/to/reembemr/path. Then I create a new file with Ctrl+N. Last time I tried to save this file, my home folder or something equally useless was preselected. So I went back to the other file and went to the Open File dialog, where the file's current path is already selected - but no way to copy it into the clipboard.

Oh, and when I want to enter a path alone, to browse the files there and then select a new file name, I entered the path, hit the Enter key and boom - the dialog was closed and an error message told me that this was a directory. Yes I Know.

(I'm a Windows user. Please tell me what I need to do differently to get the same stuff done on Ubuntu/Gnome.)

OK, you open a ***new*** file, not trying to save the old file. Well, I'm happy with the ***terminal window*** and command lines, so I open such a terminal window and change directory to /some/very/long/and/hard/to/reembemr/path. That can be done with drag and drop from the file browser Nautilus (the standard one of Ubuntu). And you are right in place.

type ```
cd {space}
``` {and drop the long path}
```
cd  /some/very/long/and/hard/to/reembemr/path
```Then run gedit from the command line:

```
gedit filename
```or if you want to detach it from the terminal window:
```
gedit filename &
```

---

### Post by ygoe on 2013-01-04
Okay, that's how I have initially opened the first file. But then I needed to create another, new file, in the same directory, or one level up or so. So I thought, well, now that I'm here, why not use what gedit can do. Once I am in gedit, am I then lost?

---

### Post by sudodus on 2013-01-04
When you open a new file, do it from the same terminal window (if you used & at the end of the command line), and it will go into the same gedit window, but with another tab :-)

---

### Post by houseworkshy on 2013-01-04
You can also right click on the path name and "select all" and copy it, then when "saving as" paste the previous address and only have to edit the end of it.

---

### Post by ygoe on 2013-01-04
Alright, so you say that Gnome or gedit are not able to give me the current path in plain text, but only in that playful not not especially beautiful buttons. Right?

---

### Post by ygoe on 2013-01-04
> **houseworkshy said:**
> You can also right click on the path name and "select all" then when "saving as" paste the previous address and only have to edit the end of it.

Oh, multiple users. So for this: There is no text to select or copy. It's just buttons. If there was text, I wouldn't ask such a question. Have you actually seen it?

---

### Post by houseworkshy on 2013-01-04
My appologies you are right, sorry about that,not sure what I was thinking of. I have used an editor which does have the option to put the location at the top web browser style.  Now I'm digging around trying to find out which one it was. Sorry about that.
 One thing though, if you select properties you can select and copy from the text in the popup itself, not just the text entry box.
There are also clip board managers like Parcellite which allow one to have and use a clipboard history.  One of those may help, I use the default Klipper in KDE.

---

### Post by ygoe on 2013-01-04
There are no properties as well. Here's a screenshot of what my window looks like:

(see attachment)

The top shows the path /etc/apache2/conf.d. I want to copy this very path into the clipboard. But it's not possible.

Also, as it turns out, pasting the path into the textbox when saving the file is also not easy, because I need to type in the new file name at the same time. When I only enter the new path but not the file name (to first browse the target directory for existing files), it fails with the error mentioned above: "This is a directory" and nothing is saved. Back to start.

Gnome seems to be for beginners. Directory management and clipboard is for the console, or Windows.

---

### Post by sudodus on 2013-01-04
> **LonelyPixel said:**
> Alright, so you say that Gnome or gedit are not able to give me the current path in plain text, but only in that playful not not especially beautiful buttons. Right?
It's a simple editor, not a file browser. You can use your file browser to create a new file by right-clicking on an empty area or via the pull-down menu

***File -- Create new document ...***

and then open it with the editor.

Edit: By the way Gnome is the desktop environment (gnome 3 in the current Ubuntu version). See this link
[http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

---

### Post by ygoe on 2013-01-04
Alright, so I'm basically back in the console.

Thanks for your efforts anyway!

---

### Post by sudodus on 2013-01-04
> **LonelyPixel said:**
> Alright, so I'm basically back in the console.

Thanks for your efforts anyway!

Many people work more efficiently with the terminal window. But if you want the GUI way, you are welcome.:-) There are convenient ways to do that too, but sometimes slightly different from Windows. This isn't Windows after all.

From the fundaments all the way to the application programs linux is built with small modules, that are good at doing some particular tasks. In this case, you wanted to do something that is not well done in the editor gedit, but you can do it easily and conveniently in a file browser window, that you have open at the same time as you are editing.

---

### Post by steeldriver on 2013-01-04
maybe I'm misunderstanding but right clicking the item in the main selection frame works for me

---

### Post by ygoe on 2013-01-04
Okay, that "Copy file's location" entry is missing in my version. Maybe 10.04 LTS is outdated again...

---

### Post by houseworkshy on 2013-01-04
Not wishing to confuse things and for when you have your tasks out of the way.  There are many editors out there.
 [http://en.wikipedia.org/wiki/Comparison_of_text_editors](http://en.wikipedia.org/wiki/Comparison_of_text_editors)
Wikipedias section on terminal emulators is also worth a read
[http://en.wikipedia.org/wiki/List_of_terminal_emulators](http://en.wikipedia.org/wiki/List_of_terminal_emulators)
Those listed as X Window terminals are valid to Ubuntu.
I  have several of them leafpad, gedit, cream, emacs, gvim, lx terminal,  konsole, and flip around them.  One of them, not nessesarily one I still  have, does have an address bar, I just can't remember which one it is.
When  you have time you could go hunting for something you like more, most  are free and severel are already in the default software repositories.
Just an aside.

There may be around it for some tasks.  The up and down arrows on your keyboard will scroll through commands used in gedit.  When doing that they will also scroll through who issued them and from where in the system.  It looks something like username@desktop:~$ followed by what ever the command was.  So if you had done something from oh anywhere say desktop/documents/stories/roughdraft you could copy the relevant part edit the end and cd to, in this example, desktop/documents/stories/roughdraft2 perhaps.  The ~ means the desktop in home so wherever you are cd ~ will always bring you back to username@desktop;~
I usually have two terminals open at the same time, one for the manual pages and one to work in.  It may help to know that one can copy and paste between terminals.
Not ideal perhaps but workable if you don't mind scrolling.

---

### Post by rewyllys on 2013-01-04
> **LonelyPixel said:**
> Okay, that "Copy file's location" entry is missing in my version. Maybe 10.04 LTS is outdated again...
Just a suggestion: You might try updating gedit with the Synaptic Package Manager, and see whether a more recent version of gedit will have the "Copy file's location" feature.  

My copy of gedit has the feature; the version is 3.4.1 (I'm using Linux Mint 13, which is based on Ubuntu 12.04).

---

### Post by ygoe on 2013-01-05
I'm using updates regularly so there won't be any news for my OS version.

On Windows, there is a shell dialog for opening and saving files that all applications can make use of. I thought this is the same for Gnome, so that most applications and editors would suffer the same issue. If Gnome doesn't have this infrastructure and every editor needs to implement their own file dialogs, that would explain why other editors can be better here. (Of course every app is allowed to implement OS dialogs on their own, but on Windows nobody does that, and when they do, things only get worse. Most corss-platform apps for example bring their own dialogs and users will have to learn them because they're different from anything else they know.)

---

### Post by iMac71 on 2013-01-05
You might try someone of the plugins you find at the following site:
[https://live.gnome.org/Gedit/Plugins](https://live.gnome.org/Gedit/Plugins)

---

