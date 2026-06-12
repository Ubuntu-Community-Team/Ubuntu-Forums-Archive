---
title: "HOWTO: Create a GUI for your Tip using Kommander"
date: 2006-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by opticyclic on 2006-04-30
This HOWTO is for the benefit of the users that don't like using Terminal/Konsole.
e.g. Windows converts who expect a dialog/GUI for everything
or for people like your grandma who want things to be as simple as possible.

However, the target audience of this HOWTO are the developers/contributers of other HOWTOs.

This will explain in several easy steps how you can package your tip/script into a simple GUI for others to use.
This is not to say that you shouldn't continue to post in the current style with the commands separated out.
But to extend what is currently done so that people have the option of the two.

This tip is based around [Kommander]("http://kommander.kdewebdev.org/") and a lot of the information has come from this [crash course in using it.]("http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/kommander-introduction.html")

**_1. Install Kommander Editor:_**
Either via Synaptic or Add Applications
It might even be installed with KDE by default.

**_2. Run Kommander:_**
(Ubuntu) Applications > Programming > Kommander Editor 
(Kubuntu) KMenu > Programming > Kommander Editor *(Not so sure of this path)*

**_3. Create a Hello World GUI:_**
[LIST=1]
[*]File > New
[*]Tools > Kommander > ExecButton (or click the icon with OK on it in the toolbar)
[*]Click on the form (the main pane on the right)
[*]Type OK in the text property in the left pane
[*]Right Click the OK button you have just created
[*]Select Edit Kommander text
[*]Type echo "Hello World"
[*]File > Save
[*]Open Terminal/Konsole
[*]kmdr-executor test.kmdr
[*]Your GUI pops up, Click OK
[*]Notice how Hello World appears in the terminal
[/LIST]

**_4. Create Your Own GUI:_**
Step 3 should have got you used to the environment.
Now all you need to do is make the GUI look like you want and paste all your commands that previously had to be type in the terminal into the "Edit Kommander Text" of the OK button (or wherever)

**NB:**
A useful widget is the FileSelector widget.
If you want to select a file and copy it all you need to do is add a FileSelector then in the Edit Kommander Text of the OK button add
```
cp "@FileSelector1.text" CopyOfText.txt
```The at-sign (@) is used to mark Kommander's special functions. 
When a script is executed, Kommander first parses it and executes all functions starting with @. 
Many functions return a value, which is then substituted for the original @function text. 
The resulting processed text is then executed as a regular shell script.

The users of your HOWTO will also have to install Kommander and they run your GUI from the terminal with ```
kmdr-executor test.kmdr
```

I have attached an example of how I took the [usplash HOWTO]("http://ubuntuforums.org/showthread.php?t=82835") and made it into a simple GUI.
Right Click the OK button and select "Edit Kommander Text" to compare what I have done to the original usplash HOWTO.

---

### Post by stalefries on 2006-05-02
Couldn't this be done with Zenity? It's included by default in Ubuntu (no idea about Kubuntu).

---

### Post by opticyclic on 2006-05-05
As far as I am aware Zenity doesn't have an IDE that lets you drag and drop controls so that you can easily design your dialog.

This screenshot of Kommanders IDE shows how easy it is to create complex dialogs
[IMG]http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/kommander-editor.jpg[/IMG]

---

### Post by d3v1150m471c on 2010-02-20
when i click the "ok" button i created as directed above i get the error message

"Error in widget ExecButton1:
Line 1: in function 'echo': too few parameters. "

How do i fix this?

---

### Post by d3v1150m471c on 2010-02-20
> **d3v1150m471c said:**
> when i click the "ok" button i created as directed above i get the error message

"Error in widget ExecButton1:
Line 1: in function 'echo': too few parameters. "

How do i fix this?

Update:

needs to be-
```

#!/bin/bash
echo "hello world"

```

---

