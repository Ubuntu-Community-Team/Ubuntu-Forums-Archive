---
title: "'CheckGmail' or other gmail notifiers?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-04-26
I currently have the program CheckGmail installed and love it. I mainly love how I can hold cursor over the icon in the top bar and it actually shows me who the emails are from the the subject. This seems to be the only gmail notifier that does this. The problem is when I shut down my computer or restart it that icon goes away and I have to go back to Applications->Internet->CheckGmail and launch it.

So my question is can I make it so CheckGmail logs me in each time my computer boots up so I do not have to launch it? I don't want the icon from the Internet menu up there since I still need to click it. I just want something that will automatically sign me in. I looked for my GmailNotifer add-on for Firefox, but sadly this Firefox that is with 8.04 doesn't support it yet.

Is there other gmail notifiers that show me the mail when I hold cursor over it? I looked and installed plenty from add/remove.

---

### Post by warbread on 2008-04-26
Go to Preferences > Sessions.  Click on 'add' and put in the necessary information.  If you need to, you can right click on the icon you already have to CheckGmail and hit 'add icon to desktop', the right click on the icon and go to 'properties'.  This will show you the information you need to add into the Session box.

---

### Post by noremac on 2008-04-30
I have used checkgmail for months now. I installed 8.04 the other night and installed checkgmail. It worked for a few days, but now I am getting errors. It wont open and if I try opening it in terminal, here is what I get:

```
cameron@cameron-desktop:~$ checkgmail
Warning: Crypt::Simple not found ...

CheckGmail requires the above packages for password encryption
Please download and install from CPAN (http://search.cpan.org) if you want to use this feature ...

Warning: Gtk2::Sexy not found ...

CheckGmail uses Gtk2::Sexy for clickable URLs in mail messages
Please download and install from CPAN (http://search.cpan.org) if you want to use this feature ...

:14: parser error : error parsing attribute name
  <label_delay [new label]="300" />
               ^
:14: parser error : attributes construct error
  <label_delay [new label]="300" />
               ^
:14: parser error : Couldn't find end of Start Tag label_delay line 14
  <label_delay [new label]="300" />
               ^ at /usr/lib/perl5/XML/LibXML/SAX/Parser.pm line 31
A thread exited while 2 threads were running.
cameron@cameron-desktop:~$ 

```

That just isn't making much sense to me. I don't know Linux ALL that well, but is it wanting a program "Gtk2" in order to work, or what?

But yeah, I use and much prefer checkgmail over any others. Really like what all you can do with it, without opening the browser.

Thanks for any help.
-Cameron

---

### Post by AndThenWhat on 2008-05-01
> **noremac said:**
> I have used checkgmail for months now. I installed 8.04 the other night and installed checkgmail. It worked for a few days, but now I am getting errors. ... 

Have you tried uninstalling it and reinstalling it?

If not open a terminal and run these commands in order:
```
sudo apt-get remove checkgmail
sudo apt-get autoremove
sudo apt-get install checkgmail
```

---

### Post by noremac on 2008-05-01
I had removed it and reinstalled it, however had not done the autoremove. I have now done so and am getting the same results.

-C

---

### Post by doorknob60 on 2008-05-01
Hmm it works fine for me, maybe try compiling it from source.

---

### Post by gandaran on 2008-05-01
> **noremac said:**
> I had removed it and reinstalled it, however had not done the autoremove. I have now done so and am getting the same results.

-C

uninstall and install the program again will never fix this problem, as the settings/configuration files remains in the home folder, all you have to do is to look for checkgmail in the hidden home folder and just delete all relating to checkgmail, then start checkgmail again.

---

### Post by noremac on 2008-05-01
> **gandaran said:**
> uninstall and install the program again will never fix this problem, as the settings/configuration files remains in the home folder, all you have to do is to look for checkgmail in the hidden home folder and just delete all relating to checkgmail, then start checkgmail again.

That was easier than we all thought. Fixed it, thanks!

-C

---

