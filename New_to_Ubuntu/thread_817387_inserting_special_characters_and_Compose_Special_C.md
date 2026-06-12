---
title: "inserting special characters and Compose Special Character extension"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by distractible on 2008-06-03
Hi! This is going to be a really, really long-winded post, so I apologize! 

I am looking for a convenient way of inserting special characters in OpenOffice.org's Writer program. I have tried the Compose key option but it only seems to offer certain accented characters, not all of them. I also tried setting my keyboard to US-International with deadkeys, but again, not all of the accented characters I need seem to be available, and I need to be able to choose when a combination like, 'a, for example, will be an a with an accent mark, and when it will be apostrophe a, and the deadkeys option doesn't seem to allow for that flexibility. 

I have not yet tried creating macros and assigning certain characters to certain key combinations, because I'm new at this and that scares me a little! 

And I don't understand the Unicode numbers--I can't seem to get them to work!

Finally, I downloaded this extension to Writer:

[http://extensions.services.openoffice.org/project/ComposeSpecialCharacters](http://extensions.services.openoffice.org/project/ComposeSpecialCharacters)

But the dialogue box that comes up when I go to Insert>Compose Character is very small, just showing part of what should be there, and I can't figure out how to expand it. 

Has anyone had luck with this extension? Or has anyone figured out a quick and convenient way of inserting special characters?

---

### Post by kaboodle_fish on 2008-06-03
There is an Add to Panel option called Character Palette 

Is that what you need?

---

### Post by Kevbert on 2008-06-03
This way may not be as quick as you want, but it works.
Go to Applications - Accessories - Character Map.  Select the character type you want (eg Latin), select the font (eg sans) and then scroll down to the character you want.  Double click on this character (plus any others) so that it appears in the 'Text to copy' box and hit copy.  Now you can paste them into a document with Ctrl+V   àáâãäåèéê
This is useful for me because if I write my surname as it should be, it ends in an é.

---

### Post by distractible on 2008-06-03
Hi! Well, I'm really hoping for keyboard shortcuts, because those darned dialogue boxes are kind of slow! When I used to use Microsoft Word, there were key combinations along the lines of Ctrl-Alt-^-u that were standard, or you could assign your own. That's what I think this OpenOffice extension is supposed to be about--but it doesn't seem to be functioning well on my system.

---

### Post by distractible on 2008-06-03
> **kaboodle_fish said:**
> There is an Add to Panel option called Character Palette 

Is that what you need?

Hi! Hm, I'm not sure. Is it different from the Character Map under Applications>Accessories and the Insert>Special Characters option in Writer?

---

### Post by kaboodle_fish on 2008-06-04
Ummm I am not sure

I did find this thread from before that may help 

[http://ubuntuforums.org/showthread.php?t=125107](http://ubuntuforums.org/showthread.php?t=125107)

---

### Post by distractible on 2008-06-04
Yep, the compose key option would be great--but it doesn't seem to work on my computer. I can get it to create á or à but no other diacritical marks, e.g. umlaut, etc. 

Does anyone know how to use the Unicode codes? I have never been able to figure out how to get those to work, either.

---

### Post by proapps on 2008-06-20
Hi there.  I'm the author of the Compose Special Characters extension.  I'm sorry to hear that you've had trouble using it.  I haven't had any reports of the dialog box causing problems so I'm really interested in trying to troubleshoot what's happening for you.  If you could supply some information that would be very helpful:

What version of OO are you using?
What version of the extension are you using (1.0.92 is the latest version)?
What screen resolution are you working with?

A screenshot would be great so I can see what you're seeing.  If you send the above by email I'll see what I can do to sort the issue out.

Chuck

---

### Post by mettlewk on 2008-06-29
Hi,

I too am finding this extremely frustrating. 
In windows os, I can choose my keyboards and rotate between them with a shift left alt combo.

Accents are real simple, if a key can be accented and you want it accented one types the accent key and then the vowel you want and the accented version of the vowel is displayed. 

The Character map is a totally unacceptable way of entering characters in a word processing environment.  way way too slow.

I have been trying to learn Spanish and the lack of documentation on how to make a latin keyboard work is again, frustrating. For a multi language supported system this seems pretty strange.  Those accents are not optional, they are integral parts of the spelling and meaning.

If standard keyboard routines for those accented characters aren't available yet, write them, they are needed; and if they are available, document it PLEASE.

---

### Post by lukjad on 2008-06-29
> **distractible said:**
> Yep, the compose key option would be great--but it doesn't seem to work on my computer. I can get it to create á or à but no other diacritical marks, e.g. umlaut, etc. 

Does anyone know how to use the Unicode codes? I have never been able to figure out how to get those to work, either.

Unicode is Ctrl+Shift+u then you type in the number and press space. For some reason OpenOffice doesn't seem to allow this command (probably because Shift+u=U and Ctrl+u=Underline). For online Ctrl+Shift+u works (&#1364;&#597;&#1109;&#1365;&#1366;).

---

### Post by lukjad on 2008-06-29
> **mettlewk said:**
> Hi,

I too am finding this extremely frustrating. 
In windows os, I can choose my keyboards and rotate between them with a shift left alt combo.

Accents are real simple, if a key can be accented and you want it accented one types the accent key and then the vowel you want and the accented version of the vowel is displayed. 

The Character map is a totally unacceptable way of entering characters in a word processing environment.  way way too slow.

I have been trying to learn Spanish and the lack of documentation on how to make a latin keyboard work is again, frustrating. For a multi language supported system this seems pretty strange.  Those accents are not optional, they are integral parts of the spelling and meaning.

If standard keyboard routines for those accented characters aren't available yet, write them, they are needed; and if they are available, document it PLEASE.

As for the Keyboard layout the best way to switch between them is this.

Right click your panel and select "Add to Panel". Then scroll down to "Keyboard Layout" and select "Add". My default was "USA". You should now see "USA" or something similar in your default keyboard layout which is now somewhere near where you right clicked. See my screenshot for an idea. Then go to System->Preferences->Keyboard->Layout and click the "Add" button. Select your other keyboard layouts you want and set a Default.You should be able to find them mostly by country and then from the choices in that country. I did find a few keyboard layouts under Latin America if that is what you were looking for. Next click Close and you should see that USA still there. Click it and you will be able to switch between keyboard layouts to your heart's content.

---

### Post by mettlewk on 2008-07-07
> **lukjad007 said:**
> As for the Keyboard layout the best way to switch between them is this.

Muchas gracias por la ayuda señor. 

Lo saludo atentamente,
Mettlewk

---

### Post by lukjad on 2008-07-10
De nada. Hasta la proxima!

---

### Post by Paddy Landau on 2008-07-11
> **proapps said:**
> Hi there.  I'm the author of the Compose Special Characters extension.  I'm sorry to hear that you've had trouble using it.  I haven't had any reports of the dialog box causing problems so I'm really interested in trying to troubleshoot what's happening for you...
I am having this problem, too...

But it's not specifically your extension. I get it with other extensions. I've created a post about this on the OO forum:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=47&t=7716](http://user.services.openoffice.org/en/forum/viewtopic.php?f=47&t=7716)

---

### Post by proapps on 2008-07-12
It turns out the problem with the dialog display was a bug in OO 2.4.  It seems to have been resolved in OO 2.4.1 - I've tested on Ubuntu 8.04.1 and it's working fine.

Please give the extension another try (current version is 1.0.92).  And please let me know if there are any other characters that should be added to the list in the extension!

Chuck
Developer of Compose Special Characters extension.

---

### Post by Paddy Landau on 2008-07-12
> **proapps said:**
>  It seems to have been resolved in OO 2.4.1 - I've tested on Ubuntu 8.04.1 and it's working fine.
Unfortunately for me, I have OO 2.4.1 and Ubuntu 8.04.1, and it still gives problems.

Bizarrely, late last night it suddenly started working; but this morning it's back to its old problems.

---

### Post by Paddy Landau on 2008-07-12
I think that I've discovered the cause of the error.

Here's the answer that (so far) has worked for me:

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=47&t=7716&p=36284#p36284](http://user.services.openoffice.org/en/forum/viewtopic.php?f=47&t=7716&p=36284#p36284)

I hope that helps other readers.

---

### Post by Samhain13 on 2008-07-12
> **lukjad007 said:**
> Unicode is Ctrl+Shift+u then you type in the number and press space. For some reason OpenOffice doesn't seem to allow this command (probably because Shift+u=U and Ctrl+u=Underline).

This works just fine in my box and OpenOffice 2.4.1. :)

---

### Post by lukjad on 2008-07-13
> **Samhain13 said:**
> This works just fine in my box and OpenOffice 2.4.1. :)
Interesting. I hoped that it might work for someone but in the event that it didn't or that searching for the Unicode number might be a bit hard, I posted the keyboard layout solution. Good to know.

---

### Post by selkie1964 on 2008-07-26
Actually, I just tried it in OpenOffice Writer and CTRL+SHIFT+U **does** work, but you have to continue holding down the CTRL and SHIFT keys while you type the unicode numbers **AND** press the spacebar.  It seems like it's not gonna work because as you're typing the U and the unicode, those characters are appearing on the screen, but as soon as you press the spacebar, your special character appears.  I tried it with both the lower-case thorn character ( þ ) and the accented lower-case e character ( è ) and both worked, no probs.  :)

Of course, if you're used to the ALT codes in Windows, you're gonna have to memorize a whole buncha new codes.  :mad:

---

### Post by Paddy Landau on 2008-07-27
> **selkie1964 said:**
> Actually, I just tried it in OpenOffice Writer and CTRL+SHIFT+U **does** work, but you have to continue holding down the CTRL and SHIFT keys while you type the unicode numbers **AND** press the spacebar.
Lucky I have three hands! LOL

It doesn't work only in OpenOffice, though. It also works in other places, such as Firefox, gedit and gnome-terminal. Obviously, Ctrl-Shift+U is a Linux or Gnome thing.

I also notice that AltGr-<key> (e.g. AltGr-5) produces a range of characters, and AltGr-Shift-<key> yet another. It's worth experimenting with and perhaps annotating your keyboard!

---

### Post by selkie1964 on 2008-08-17
> **Paddy Landau said:**
> 
I also notice that AltGr-<key> (e.g. AltGr-5) produces a range of characters, and AltGr-Shift-<key> yet another. It's worth experimenting with and perhaps annotating your keyboard!

Um, what is AltGr?  :confused:

---

### Post by Paddy Landau on 2008-08-17
> **selkie1964 said:**
> Um, what is AltGr?  :confused:
On Windows-style keyboards, you'll find a key labelled AltGr.

Windows usually (but not always) treats it exactly the same as pressing Ctrl-Alt. However, I've found that Linux does not do this.

I don't know if non-Windows keyboards have an equivalent.

---

### Post by scottiw2000 on 2011-08-08
If anyone is reading this old thread (it ranked high in Google), you might find two pieces of information helpful. First, the ctrl+shift+u key combination works very well in the current versions of LibreOffice (used to be OO). You don't have to hold down any keys while you type the numbers for the character code.

Second, there's a great app called AutoKey that lets you set global keyboard shortcuts and snippets (like Textexpander on OSX or iOS) and runs in the background. You can easily use AutoKey to set up whatever keyboard shortcuts you want to insert any unicode character.

---

### Post by Paddy Landau on 2011-08-08
@scottiw2000: Thanks for that.

I now use Drawer on my panel, and put Character Palette inside it.

In LibreOffice (or OpenOffice if you prefer), I use a lovely extension, [Compose Special Characters]("http://extensions.services.openoffice.org/en/project/ComposeSpecialCharacters"), which makes it a doddle to remember keystrokes.

---

