---
title: "[SOLVED] Run a file in Terminal from an icon?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by L a r r y on 2008-06-23
I have developed a script that I can run on my desktop to encode email address character strings (email@example.com) and have them come out as &#x65;&#x6D;&#x61;&#x69;&#x6C;@&#x65; ... gobbledygook which I can copy to clipboard and insert in my HTML, and which is rendered in human-readable form on the browser.

(Oops, still work to be done, I failed to convert the @)

My script uses the perl -e switch, and is contained between a set of single quotes.  It is saved as a file on my desktop, made executable and runs in the Terminal.

I double-click my icon to start the file, and have the "run in terminal, display, cancel or run" choices dialog pop up.  I want to run it in Terminal without being prompted each time I start the file.

My question then is, how to accomplish this?
Many thanks in advance.

---

### Post by Vivaldi Gloria on 2008-06-23
You can change it in nautilus settings, look at the second tab.

---

### Post by RomeReactor on 2008-06-23
Hi. Create a new launcher and fill it out like this:

* Type: Application
* Name: *******
* Command: gnome-terminal -e /full/path/to/file
* Comments: ************

---

### Post by L a r r y on 2008-06-23
> **RomeReactor said:**
> Hi. Create a new launcher and fill it out like this:

* Type: Application
* Name: *******
* Command: gnome-terminal -e /full/path/to/file
* Comments: ************

Works like a charm!  Thank you!  I moved my target file into my home and off my desktop, then put the launcher there.

I guess what I was missing was what the Terminal is called on the command line.

---

### Post by L a r r y on 2008-06-23
> **Vivaldi Gloria said:**
> You can change it in nautilus settings, look at the second tab.

OK, I see that -- I opened my home folder and went to the window menubar:   Edit > Preferences to open the tabbed dialog.  

There are two Run options, besides Display and Cancel -- one is Run in Terminal and the other is Run.  

I set the behavior to run executable text files, and double-clicked the copy of my script still on the desktop.  That did not perform the Run in Terminal option, but instead performed the Run option, which did nothing.

So I have set the option back to Always Ask.

Nautilus is the equivalent to Microsoft's Windows Explorer, the windowing manager, in case anyone else is reading these posts and not familiar with the local terminology!:)

Thank you for your input.

---

### Post by L a r r y on 2008-06-25
> **RomeReactor said:**
> Hi. Create a new launcher and fill it out like this:

* Type: Application
* Name: *******
* Command: gnome-terminal -e /full/path/to/file
* Comments: ************

I have a problem!  (Edit:  The whole thing cropped up because somewhere along the way a space got introduced in front of the #! she-bang, as I noticed when I was about to post the program code -- AAAGH!  Such a waste of time!)

This solution worked beautifully until I decided to cut the perl script from the desktop and move it up one level to my account home.  I removed Desktop/ from the path in the launcher, and fired it up.

Window comes up and goes away.  Double click the perl script and am asked the four choices, and choose to run in terminal.  Window comes up and goes away.

Start terminal, and launch the file from the command line.  The script runs just fine.

Properties, I checked permissions, read-write, read, read, and checkmark to make executable checked.

Rewrote the launcher command line, restarted the computer, moved the script to the desktop and added the Desktop/ back into the path, renamed the file too.  I even used the Browse button to rewrite my path and re-inserted gnome-terminal -e, space on either side of -e.  In rewriting gmpme-terminal, misspelled, I got a notice that there was no such command, and corrected it to gnome-terminal.  Back to the same thing.

I have seen the window come and go away when I had errors in the program script, and by running it from the terminal I got to see the error messages.  


The script runs perfectly from the terminal.  What am I missing here?

---

### Post by RomeReactor on 2008-06-25
That's odd. Please post the entire line you're using in the launcher; maybe we can see what's going on there.

---

