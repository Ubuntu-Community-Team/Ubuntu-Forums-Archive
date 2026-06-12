---
title: "[SOLVED] Mailto: Obfuscator for Linux?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by L a r r y on 2008-06-01
Hello,
I have for several years been editing a web site using Windows third-party software, hand-coding all the way.  I had an Apache server, running a Perl installation at **c:\usr\bin\perl.exe**, so that I could write my Perl scripts with the same she-bang I need on my Linux-hosted Apache server-equipped web site.  Only difference between my local web site and the one on the Web, I didn't need to chmod anything in Windows.  And with my software I could directly save .htaccess without Windows' squawking that I need a file name!

I am using Ubuntu 8.04, and found Bluefish for a Web editor.  Only thing I have not done is install Apache, and I see that I don't need to install Perl, because it's already here.

I need some help with the process of routinely converting a **mailto:email@example.com** to **&#xx;&#xx;** HTML entities.

[COLOR="DarkRed"]**Mailto: Obfuscator**[/COLOR] was an easy tool to use in Windows:  Write the plain-text email link in the Web document, highlight it, **ctrl-C**, open Mailto: Obfuscator, **ctrl-V**, **Tab**, **ctrl-C**, return to my editor, **ctrl-V**.

My highlighted string of characters was now a string of entities.

With that protection and a list of banned spambots in my root .htaccess, I have had very little in the way of spam.

My next hope is to find a way in my Bluefish to easily create **[COLOR="DarkRed"]&nbsp;[/COLOR]** as I had edited my Arachnophilia 4.0 for Windows keyboard macros to use **ctrl-space** to create that.  Its most common use in my writing is to have a double-space after ends of sentences and after colons.

Any helpful hints will be greatly appreciated!  Thanks in advance.
Larry

---

### Post by dracayr on 2008-06-01
If I understood you correct, all you want to do is convert a string into HTML Entities? You could simply use an online script like 

[http://snarkles.net/scripts/sneak/sneak.php](http://snarkles.net/scripts/sneak/sneak.php)

(use google to find others)

dracayr

---

### Post by L a r r y on 2008-06-01
That is true, I could utilize one of many online scripts to perform my encryption, but I choose to not expose my users' email addresses to the *possibility* that the site I use is logging my input for its own purposes.

So if I can find a solution that runs on my computer, I would be grateful. Otherwise, I might just take a dive into Perl and see what I can cook up!

---

### Post by dracayr on 2008-06-01
well if you have a server with php support, you could just download the script (there's a link at the bottom of the page). But, seriously, I don't think that there are spambots which scan your input, etc.. It's just as easy to scan for html-encoded email addresses...

dracayr

---

### Post by UBUSNAFU on 2008-06-01
I think L a r r y is more concerned about the intention of the obfuscation site and the coding of it dracayr. Nice security awareness L a r r y. :biggrin:

Now if you had picked almost anything but Perl I would not have minded joining you in the project. Not one of my strong points I am afraid but it really is the most secure option. Unfortunately I am also a bit of a noob at Linux programming but in Windows I would try something that intercepts the key sequences Ctrl-C Ctrl-V or T for translate and I for insert. Less keystrokes and I am sure they have something that can do a keyboard hook on these things. :)

---

### Post by L a r r y on 2008-06-25
I have written a perl script that will turn my email addresses into &#x**; representations that can be acted on by a browser as if they were plain text, which runs in the terminal window.  Work to be done to make it a little more user-friendly. If I need any further help I will open a new thread.

---

