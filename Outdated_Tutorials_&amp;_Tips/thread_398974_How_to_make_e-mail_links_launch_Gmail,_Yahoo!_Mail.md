---
title: "How to make e-mail links launch Gmail, Yahoo! Mail, or other webmail"
date: 2007-04-01
forum: Outdated Tutorials &amp; Tips
---

### Post by mssever on 2007-04-01
As a Gmail user, I was annoyed by Evolution or Thunderbird popping up every time I clicked on a mailto link. So, I wrote a set of scripts that make e-mail links open up in **Gmail**, instead. They also support **Yahoo! Mail**, **Hotmail**, **Mail.com**, **Netscape Mail**, **Opera Mail**, **Horde**, and **Squirrel Mail**. The scripts can be easily extended to use other webmail services. Note: I've only tested this with Gmail and Yahoo! Mail as they're the only two webmails that I have accounts with. Version 1.5 includes correct (I hope) support for Hotmail, thanks to ljungkvist.

Firefox users should see the "Firefox Extensions" section below for alternative methods that you might prefer.

For those of you who prefer German over English, sputnikrock has posted [instructions in German]("http://forum.kubuntu-de.org/index.php?topic=9071.0").

**[SIZE=4]Installation[/SIZE]**

Installation is simple. Note that I'm a Gnome user, so I'm not familiar with KDE or XFCE. If something doesn't work in your non-Gnome environment of choice, I probably don't know how to fix it, but I'd be glad to include your solution in this post (hint, hint).
[LIST=1]
[*]Download the attached file (gmail_link-1.5.tar.gz), extract it, and dump the files somewhere in your PATH. I suggest putting them  in /usr/local/bin. (Note: In these instructions, I'm assuming that you're installing the files in /usr/local/bin. If you put them somewhere else, adjust the instructions accordingly.)
[*]Grab [FONT=Courier New][COLOR=#ff0000]p-shortcut[/COLOR][/FONT] from [my repository]("http://repository.scottseverance.us:8066/falcon/dists/main/scripts/") and install it. You can add my repo to /etc/apt/sources.list so that you'll automatically get any updates (see instructions on the site) or you can install just the p-shortcut deb. [SIZE=1]Note: You can forget about this dependency if you don't use the file gmail_link_select_browser. However, I'm not going to take the space to document that here.[/SIZE]
[*]Make sure that each of the files is executable. ```
cd /usr/local/bin
sudo chmod +x gmail_link*
```
[*]If you use a webmail provider other than Gmail (the default), see the section "Enabling Other Webmail Services" below.
[*]*Gnome users:* Launch System > Preferences > Preferred Applications and set the mail reader to [FONT=Courier New][COLOR=#ff0000]Custom[/COLOR][/FONT]. Set the command to ```
gmail_link_select_browser "%s"
```**[SIZE=1][COLOR=#808080]Alternate method:[/COLOR][/SIZE]**
[LIST=1]
[*][SIZE=1][COLOR=#808080]Launch gconf-editor[/COLOR][/SIZE]
[LIST=1]
[*][SIZE=1][COLOR=#808080]Go to Applications > System Tools > Configuration Editor (if there is no such menu item, enable it in System > Preferences > Menu Layout); **or**[/COLOR][/SIZE]
[*][SIZE=1][COLOR=#808080]Hit <Alt>F2 and type [/COLOR][/SIZE][FONT=Courier New][SIZE=1][COLOR=#808080]gconf-editor[/COLOR][/SIZE][/FONT][SIZE=1][COLOR=#808080]; **or**[/COLOR][/SIZE]
[*][SIZE=1][COLOR=#808080]Open up a terminal and type [/COLOR][/SIZE][FONT=Courier New][SIZE=1][COLOR=#808080]gconf-editor &[/COLOR][/SIZE][/FONT]
[/LIST]
 
[*][SIZE=1][COLOR=#808080]In gconf-editor, navigate to [/COLOR][/SIZE][FONT=Courier New][SIZE=1][COLOR=#808080]/desktop/gnome/url-handlers/mailto[/COLOR][/SIZE][/FONT][SIZE=1][COLOR=#808080] and set the [/COLOR][/SIZE][FONT=Courier New][SIZE=1][COLOR=#808080]command[/COLOR][/SIZE][/FONT][SIZE=1][COLOR=#808080] key to [FONT=Courier New]gmail_link_select_browser "%s"[/FONT][/COLOR][/SIZE]
[/LIST]
 
[*]*KDE users:* (Thanks to sputnikrock for this.) Launch System Settings > Default Applications and set the mail reader to [FONT=Courier New][SIZE=2][COLOR=Red]Use a different client[/COLOR][/SIZE][/FONT]. Set the command to 
```
gmail_link_select_browser "%s"
```
[*]*Opera users (regardless of your desktop environment):* Launch Opera and go to Tools > Preferences > Advanced > Programs. Set the mailto handler to ```
gmail_link %r opera
```
[*]Visit the [mailto link test page]("http://www.scottseverance.us/mailto.html") to confirm that your webmail links are now working.
[/LIST]
[SIZE=4]**Configuration**[/SIZE]

**General Configuration**
Let's look first at the configuration options in gmail_link_select_browser. Gecko-based browsers (Firefox, Epiphany, Galeon) all use the same gconf setting. That means that it isn't possible to find out which browser is in use when you click a mailto link (if I'm wrong about this--and I hope I am--please enlighten me).

If you never have multiple browsers open simultaneously, all you have to do is make sure that any browsers you use are listed in the [FONT=Courier New][COLOR=#ff0000]browserList[/COLOR][/FONT] variable in the first section of the file.

If you do use multiple browsers at the same time, prioritize the [FONT=Courier New][COLOR=#ff0000]browserList[/COLOR][/FONT]. The Gmail window will open in the first browser in the list that is currently running. This might not be the browser you're actually using due to the limitation explained above. So, you might want to adjust the order of the browsers. *Note that links clicked in Opera will always open in Opera, regardless of this setting*.

**Enabling Other Webmail Services**
*Currently-Supported Webmail Services*
The file gmail_link contains support for multiple webmail services beginning with version 1.2. Switching services is simply a matter of finding the configuration section near the top of the file and uncommenting the appropriate service's [FONT=Courier New][COLOR=#ff0000]formatString[/COLOR][/FONT] line. There are instructions in the file.

*Services Which Are Not Supported*
To enable a webmail service that isn't currently supported, you'll first need to determine the proper URL to use, and then set it in the configuration section of the file gmail_link. Technically-inclined users can see the comments there for instructions. Please post the fruits of your labors so that I can include additional webmail services in a future version of the script.

If you're not technically inclined, fire up a browser on a computer that opens mailto links in your webmail of choice and visit the [mailto links test page]("http://www.scottseverance.us/mailto.html"). Click on the [FONT=Courier New][COLOR=#ff0000]E-mail 3[/COLOR][/FONT] link and the [FONT=Courier New][COLOR=#ff0000]E-mail 4[/COLOR][/FONT] link and post the addresses of the pages that pop up. Then I (or someone) will format it properly and update the scripts.


[SIZE=4]**Browser notes**[/SIZE]

**Gecko-based Browsers (Firefox, Epiphany, Galeon, etc.)**
Links might not always open in the expected browser. See the General Configuration section above for details.

**Opera**
If you click a mailto link in Opera, it will always open in Opera--unlike Gecko-based browsers. There is no need to prioritize the browser list for Opera's sake.

**Konqueror**
This script works with Konqueror, but Gmail doesn't (as far as I can tell). If you use a webmail service other than Gmail, you can use this script--provided that you enable that service (see the Configuration section).

To enable the script in Konqueror, start KDE's system settings program and choose Default Applications > Email Client. Check [FONT=Courier New][COLOR=#ff0000]Use a different email client[/COLOR][/FONT] and enter ```
/path/to/gmail_link_select_browser
```I'm not a KDE user, so I don't know if this will have side-effects. KDE users, please enlighten me.


[SIZE=4]**Firefox Extensions**[/SIZE]

**Gmail Manager**
Thanks to liljoe76 for mentioning [Gmail Manager]("http://www.longfocus.com/firefox/gmanager/"). If you use Gmail and Firefox, it's quite a thorough solution. I've installed it alongside my script and disabled its mailto link option because I want to have mailto links work in all browsers, not just Firefox.

[SIZE=2]**WebmailCompose**[/SIZE]
Yopnono pointed me to the Firefox extension [WebmailCompose]("https://addons.mozilla.org/en-US/firefox/addon/206"). It's another option if you use Firefox 1.5 or lower. I haven't tried it as I use Firefox 2.0.

**Pros**
[LIST]
[*]As a Firefox extension, links will always open up in Firefox.
[*]Installation is presumably simpler.
[/LIST]
**Cons**
[LIST]
[*]It appears to be abandonware; the last version was released 2005-09-16.
[*]The Yahoo! Mail format string is incorrect, causing some links to work incorrectly. Other webmail services might have incorrect format strings, as well. [SIZE=1](I've taken a number of format strings from WebmailCompose for use in my own script. While I've fixed the Yahoo! Mail string in my script, any errors in the other string are present in mine, as well, since I don't have accounts with the other providers to test with.)[/SIZE]
[*]WebmailCompose only works in Firefox; users of Epiphany, Opera, etc. will need a different solution.
[*]WebmailCompose doesn't work in Firefox 2.0, the current version of Firefox. That means that Dapper users might be OK, but Edgy amd Feisty users are out of luck.
[/LIST]
**[SIZE=4]Change Log[/SIZE]**
[LIST]
[*]1.5 (2008-06-11): Thanks to ljungkvist, Hotmail now works correctly (I hope).
[*]1.4 (unknown date, possibly 2008-02-14): Somehow, I missed updating this post for 1.4, and I have no change log entries for it. I believe it has something to do with supporting Google Apps mail, though, thanks to MountainX.
[*]1.3 (2007-06-04): I finally figured out how to fully support Opera. The file gmail_link_opera is no longer necessary.
[*]1.2 (2007-04-03): Added support for Yahoo! Mail, as well as several other webmail services that I haven't tested: Hotmail, Mail.com, Netscape Mail, Opera Mail, Horde, and Squirrel Mail.
[*]1.1 (2007-04-02): Added support for CC and BCC. I've never seen these kinds of links in the wild, but since they're theoretically possible, I support them. gmail_link should now support every kind of link supported by Gmail.
[*]1.0 (2007-04-01): Initial public release
[/LIST]

---

### Post by mssever on 2007-04-02
I've updated this script to support all the possible types of links (I hope).

I'm hoping someone can supply the necessary info so that I can support Yahoo! Mail and Hotmail, as well.

---

### Post by yopnono on 2007-04-03
Or for Firefox you can use an add-on called  WebmailCompose

---

### Post by mssever on 2007-04-03
Thanks for the mention. For some reason, I didn't find that extension while I was searching. Maybe it was because I used Gmail as one of my search terms. At any rate, I've released a new version and updated the thread to take advantage of the information.

As I pointed out in my revised post, WebmailCompose works in some situations, but it's buggy and my scripts are much more versatile. If WebmailCompose works for you, great.

---

### Post by liljoe76 on 2007-04-03
not to, in any way 'dis' your script. but for firefox i use this extension.
[http://www.longfocus.com/firefox/gmanager/](http://www.longfocus.com/firefox/gmanager/)

---

### Post by mssever on 2007-04-03
> **liljoe76 said:**
> not to, in any way 'dis' your script. but for firefox i use this extension.
[http://www.longfocus.com/firefox/gmanager/](http://www.longfocus.com/firefox/gmanager/)

Thanks for the link! For someone who only uses Firefox, it looks to be a better solution than my script. I've updated my post accordingly.

However, because Gmail Manager only works in Firefox (and only with Gmail), my script still has its place.

---

### Post by sirlancelot on 2007-04-03
This is great! I got the script to work in Kubuntu Edgy. One (major) issue I haven't resolved is:

How do I get Firefox to work with this script? Since it's technically a gnome (or gtk?) app, nothing happens when I click on a mailto link.. I don't have Kontact installed.

---

### Post by mssever on 2007-04-03
> **sirlancelot said:**
> This is great! I got the script to work in Kubuntu Edgy. One (major) issue I haven't resolved is:

How do I get Firefox to work with this script? Since it's technically a gnome (or gtk?) app, nothing happens when I click on a mailto link.. I don't have Kontact installed.

In which browser did you get it to work? Konqueror?

I'm not very familiar with KDE, so I don't know if my suggestions will be very helpful. First, do you have gconf-editor installed? It's part of GNOME, but you might have gotten it with some GNOME stuff sometime. If so, use it (see the instructions in the first post).

Failing that, see if Firefox respects the method in my instructions for Konqueror.

Otherwise, there must be some setting somewhere that will do the trick--unless the KDE philosophy expects programs to maintain all their own configuration.

A final option if you use Gmail is to use the Gmail Manager Firefox extension mentioned in the first post.

BTW: Firefox is actually an XUL app that someone made to look like  a GNOME/GTK app.

---

### Post by mssever on 2007-04-04
Big oops...

I forgot to list a required dependency. Be sure to read step 3 of the first post for the dependency p-shortcut. If you only ever use Firefox, you probably wouldn't get bitten by this, but why take chances?

---

### Post by josephus on 2007-04-06
Great! This is nearly exactly what I was looking for.  Is there a way to attach files as well?

---

### Post by wyth on 2007-04-06
If you use greasemonkey, there's a few different scripts for this as well.  There's some for Gmail, and others for Yahoo Mail; I'm sure there's some for other web -based email clients.  I guess it all depends on what level of your system you want such a hack/script to reside.

---

### Post by mssever on 2007-04-08
> **josephus said:**
> Great! This is nearly exactly what I was looking for.  Is there a way to attach files as well?
I doubt it. First, I don't know if there's a well-supported way to formulate such a mailto link. If I really wanted to, I could read the spec, but there's another reason why automatic file attachments won't work with webmail: As a security measure, web browsers don't allow the value of a file upload field to be pre-populated, or set by Javascript. This is so some malicious site can't upload someone's passwords (or credit card details, or whatever else they want) without their knowledge. And without pre-populating a file upload control, there's really no other way to do attachments in webmail.

> **wyth said:**
> If you use greasemonkey, there's a few different scripts for this as well.  There's some for Gmail, and others for Yahoo Mail; I'm sure there's some for other web -based email clients.  I guess it all depends on what level of your system you want such a hack/script to reside. Thanks for the tip. I've never used Greasemonkey myself.

---

### Post by allforcarrie on 2007-04-10
why not just set your homepage as gmail or use a bookmark?:lolflag:

---

### Post by mssever on 2007-04-10
> **allforcarrie said:**
> why not just set your homepage as gmail or use a bookmark?
Because that doesn't make mailto: links open up in Gmail--which is the whole point of this thread.

---

### Post by Mairi on 2007-04-22
Apparently I am the only one who said...other. I use linuxmail.org mostly, though I do have Gmail and Hotmail accounts. I have to be reminded to check hotmail, and I use Gmail mostly for storage type things. My needs are simple and I don't use email clients.

---

### Post by slayerboy on 2007-04-22
Thanks, this is helpful stuff here for people who use web-based email!

---

### Post by argie on 2007-05-10
Incidentally, Konqueror works somewhat with Gmail if you either spoof the UA string to Firefox or if you append ?nocheckbrowser at the end of the gmail URL.

---

### Post by ep2011 on 2007-05-10
What im using and it seems to work fine is to download it, and only use gmail_link. I put that in my home folder, and made it executable ```
chmod +x gmail_link*
```

I then went to System -> Preferences -> Preferred Applications. I went to mail reader, selected custom, and typed: ```
/home/*user*/gmail_link.sh %s
```

It works perfectly.

---

### Post by mssever on 2007-05-10
> **argie said:**
> Incidentally, Konqueror works somewhat with Gmail if you either spoof the UA string to Firefox or if you append ?nocheckbrowser at the end of the gmail URL.

Are you using Feisty? When I tried Konqueror, neither of those methods worked for me. I was using the Edgy version (I still haven't upgraded, but I plan to do so soon). If Konqueror does in fact work in Feisty, I'll update the HOWTO.

PS: I'm not a KDE user (and I personaly loathe Konqueror), so it's entirely possibly that I simply did something wrong due to unfamiliarity.

---

### Post by mssever on 2007-05-10
> **ep2011 said:**
> What im using and it seems to work fine is to download it, and only use gmail_link. I put that in my home folder, and made it executable ```
chmod +x gmail_link*
```I then went to System -> Preferences -> Preferred Applications. I went to mail reader, selected custom, and typed: ```
/home/*user*/gmail_link.sh %s
```It works perfectly.

 Thanks for the tip about the preferred applications app. I didn't know about it, but I'll be adding it to the howto shortly. (I have a tendency to assume that GNOME settings programs are too feature-free to be useful [witness GNOME's screensaver configurator], so sometimes I overlook a useful app.)

 Also, for those who might have tried to download [p-shortcut]("http://severance.homelinux.org:8066/falcon/dists/main/scripts/") (the dependency for gmail_link_select_browser) from my repository and found it down, my server's back up. I recently moved, and had a real time of it getting Internet access. My server was offline for close to three weeks. I'm online now, but I have a slow connection.

---

### Post by argie on 2007-05-13
> **mssever said:**
> Are you using Feisty? When I tried Konqueror, neither of those methods worked for me. I was using the Edgy version (I still haven't upgraded, but I plan to do so soon). If Konqueror does in fact work in Feisty, I'll update the HOWTO.

PS: I'm not a KDE user (and I personaly loathe Konqueror), so it's entirely possibly that I simply did something wrong due to unfamiliarity.

Oh, sorry. No, I'm using the LTS release, Dapper 6.06.1 with KDE installed. That's Konqueror 3.5.4

---

### Post by ep2011 on 2007-05-13
> **mssever said:**
> Thanks for the tip about the preferred applications app. I didn't know about it, but I'll be adding it to the howto shortly. (I have a tendency to assume that GNOME settings programs are too feature-free to be useful [witness GNOME's screensaver configurator], so sometimes I overlook a useful app.)


No Problem. It just seemed like an easier and more hassle-free way of doing it.

---

### Post by mssever on 2007-06-04
I've just released gmail_link 1.3. Opera is now fully supported. If you don't use Opera, then there's really no reason to upgrade. Opera users, however should upgrade since version 1.3 fully supports all kinds of e-mail links--including those that specify a subject, body, etc.

Installation instructions are on the first post.

---

### Post by sputnikrock on 2007-08-12
> **mssever said:**
> 
Installation is simple. Note that these instructions are GNOME (Ubuntu)-specific. If you use KDE (Kubuntu) or XFCE (Xubuntu), you're on your own.

Oh... could you please add that it works with other enviroments? - It is also nearly the same way of activating it in KDE. Also the keywords are similar. This is the way in short:
[QUOTE=Keywords for KDE]5. Launch "System Settings" > Default Applications and set the mail reader to "Use a different client". Set the command to 
Code:
gmail_link_select_browser "%s"
[/QUOTE]

So this is just one step shorter in KDE. The rest is the same.

Thank you very much for your great solution! - Especially for your work with Opera wich I favour!

:)

---

### Post by mssever on 2007-08-12
> **sputnikrock said:**
> Oh... could you please add that it works with other enviroments? - It is also nearly the same way of activating it in KDE.
Thanks for posting the instructions. I've updated the tutorial.
> Thank you very much for your great solution! - Especially for your work with Opera wich I favour!
Opera is a different beast, that's for sure. I'm just glad I got it working in Opera.

---

### Post by AndrewGene on 2007-08-15
I use hotmail and when i click on your test links it does take me directly to hotmail (now windows live mail) *i'm very happy that it takes me to windows live mail btw* but it doesn't actually enter in the address or subject or anything.  It just takes me to the main page.  Any ideas??

---

### Post by mssever on 2007-08-15
> **AndrewGene said:**
> I use hotmail and when i click on your test links it does take me directly to hotmail (now windows live mail) *i'm very happy that it takes me to windows live mail btw* but it doesn't actually enter in the address or subject or anything.  It just takes me to the main page.  Any ideas??

That's probably a bug in the Hotmail format string (line 55 of gmail_link). I took several of the format strings from the WebmailCompose Firefox extension. I had to fix WebmailCompose's Yahoo format string, but I haven't tested Hotmail as I don't have a Hotmail account.

In order to fix that format string, we need to determine what that string *should* be. There are several options here:[LIST]
[*]Fiddle with the currently-existing string. For example, switching the To, Subject, etc. parts to lower case might do the trick, as might trying various combinations of abbreviations.
[*]There must be a Windows program, probably provided by Microsoft, that makes mailto: links open in Hotmail. If you can get your hands on such a program, you should be able to click on the links on my test page and snap up the resulting URLs. Those can then be turned into a proper format string.
[*]If there's a Firefox extension or a Grease Monkey script that accomplishes enables Hotmail mailto: links, then it should be possible to get the format string from there.[/LIST]If you find something, post the fruits of your labors here and I'll release an updated version of Gmail Link that correctly supports Hotmail.

---

### Post by mssever on 2007-08-15
> **AndrewGene said:**
> I use hotmail and when i click on your test links it does take me directly to hotmail (now windows live mail) *i'm very happy that it takes me to windows live mail btw* but it doesn't actually enter in the address or subject or anything.  It just takes me to the main page.  Any ideas??

Try changing the format string on line 58 of gmail_link to ```
http://by124w.bay124.mail.live.com/mail/EditMessageLight.aspx?to=%s&subject=%s&body=%s&cc=%s&bcc=%s
```Let me know if that works. I got this link from the Firefox extension GmailThis. I had to make a few guesses, though, since GmailThis has a somewhat different focus and didn't provide a complete enough link.

---

### Post by AndrewGene on 2007-08-15
> **mssever said:**
> Try changing the format string on line 58 of gmail_link to ```
http://by124w.bay124.mail.live.com/mail/EditMessageLight.aspx?to=%s&subject=%s&body=%s&cc=%s&bcc=%s
```Let me know if that works. I got this link from the Firefox extension GmailThis. I had to make a few guesses, though, since GmailThis has a somewhat different focus and didn't provide a complete enough link.

That worked perfectly except it also puts a single semi-colon in the CC: field.

---

### Post by mssever on 2007-08-16
> **AndrewGene said:**
> That worked perfectly except it also puts a single semi-colon in the CC: field.

That's odd. Does it put the semicolon in every link? Or just some? Put another way, if you visit the [mailto: link test page]("http://www.scottseverance.us/mailto.html"), which test links show a single semicolon?

---

### Post by AndrewGene on 2007-08-16
> **mssever said:**
> That's odd. Does it put the semicolon in every link? Or just some? Put another way, if you visit the [mailto: link test page]("http://www.scottseverance.us/mailto.html"), which test links show a single semicolon?

Yes it does it on all four links on the test page...I'm baffled.

---

### Post by mssever on 2007-08-16
> **AndrewGene said:**
> Yes it does it on all four links on the test page...I'm baffled.

If my memory serves me correctly, Outlook separates email addresses with a semicolon instead of a comma. Does Hotmail do likewise? And does the semicolon cause problems or is it merely unsightly? When you click on the test link that includes a CC address, does that address get entered into the CC field?

I suppose it's possible that I got the CC field name wrong in the format string. That's one of the things I guessed about. Tweaking it might make a difference.

---

### Post by kaston on 2007-12-21
i installed the gmail manager plugin but when i clicked on mailto links, evolution would still keep opening, so i uninstalled evolution using synaptic, but now when i click mailto links nothing happens.  i left the option to use gmail for mailto links checked when installing the plugin.  what am i doing wrong?

---

### Post by mssever on 2007-12-21
> **kaston said:**
> i installed the gmail manager plugin but when i clicked on mailto links, evolution would still keep opening, so i uninstalled evolution using synaptic, but now when i click mailto links nothing happens.  i left the option to use gmail for mailto links checked when installing the plugin.  what am i doing wrong?

It may be a misconfiguration, or it may be a bug in Gmail Manager. I don't use that feature, so I can't say. You should ask on the Gmail Manager thread on the Mozilla forum.

Alternatively, my script isn't affected in the slightest by evolution's presence. You could try that.

---

### Post by lespaul_rentals on 2007-12-21
Good work, mate. 

:KS:KS:KS:KS:KS

---

### Post by Wellconnected on 2007-12-24
I am having trouble with hotmail - now windows live mail.
This is an Ubuntu setup for my aunt, so the fewer unpredictable things the better.

When I click on a link I get taken to a site that says:
"Impossibile completare la richiesta. Microsoft potrebbe contattarti in relazione ai problemi segnalati."

which roughly translated as:

"Could not complete request. Microsoft might contact you about the flagged up problems".

Has anyone got a currently working string for me to try?

Thanks,
Riddick

---

### Post by MountainX on 2008-01-24
Has anyone tested this with Google Apps (GAFYD)? My gmail account is [email]myname@mycompany.com[/email]. Is this supported?

Also, I have email accounts at more than one company (all using Google Apps). Is there a way to easily specify through which domain I wish to send a particular email?

Thanks

---

### Post by MountainX on 2008-01-24
So far (with limited testing) it seems like changing the format string in the gmail_link file will enable the script to work with GAFYD. Example:

formatString="https://mail.google.com/a/my-domain.com/?view=cm&ui=1&fs=1&tf=1&to=%s&su=%s&body=%s&cc=%s&bcc=%s"

(I don't know if there is an easy solution for multiple GAFYD accounts yet.)

---

### Post by mssever on 2008-01-24
> **MountainX said:**
> Has anyone tested this with Google Apps (GAFYD)? My gmail account is [EMAIL="myname@mycompany.com"]myname@mycompany.com[/EMAIL]. Is this supported?
I haven't tested it, but if you change line 52 of gmail_link (the formatString variable) to use your Google Apps hostname, it will probably work. You might have to experiment a bit, though. If you find something that works, let me know and I'll release a new version with support for Google Apps.
> Also, I have email accounts at more than one company (all using Google Apps). Is there a way to easily specify through which domain I wish to send a particular email?Not through gmail_link. The easiest thing would be to configure Gmail to allow you to send email from multiple addresses, then select the address you want to send from after clicking a mailto link.

---

### Post by MountainX on 2008-01-24
Thanks for your reply. With my format string listed above, all for of your test mailto links work correctly.

---

### Post by mssever on 2008-01-24
> **MountainX said:**
> Thanks for your reply. With my format string listed above, all for of your test mailto links work correctly.
Thanks. I'll include the string shortly.
> **MountainX said:**
> (I don't know if there is an easy solution for multiple GAFYD accounts yet.)
I just thought of one way that might work. You could add some code to gmail_link that would bring up a zenity dialog with a list of choices. Then, you could add some logic to set the formatString variable according to the user's choice.

I'm not particularly interested in implementing such a feature, but if you write it, I'll consider including it as an option. The default, of course, should be to not bother the user with questions.

---

### Post by MountainX on 2008-01-24
> **mssever said:**
> Thanks. I'll include the string shortly.
.

It has to be edited for each user's domain name, of course. Replace "my-domain.com" with the person's Google Apps domain.

Furthermore, in GAFYD there is a way to pass the username of the email account as a parameter. I found it wasn't necessary. But I think that is because I also use Gmail Manager, which keeps me signed in to my Google Apps gmail account. So this format string works correctly without the username parameter. I suspect a final version that satisfies a wider audience may need some refinement beyond what I have provided.

---

### Post by mssever on 2008-01-24
> **MountainX said:**
> Furthermore, in GAFYD there is a way to pass the username of the email account as a parameter.
Probably that's only necessary if you use multiple accounts on the same domain. I just tested the format string with my Google Apps account that I never use, and it simply gave me a login screen. After I logged in, it sent me to the proper send mail page. If you know how to pass the username, then I can include it, but otherwise, I don't think that it's very necessary.

---

### Post by ljungkvist on 2008-06-10
I downloadeded the 'gmail_link' file, put it in my ~/bin folder, and set the default e-mail application to launch this script. Since I use hotmail (windows live...) I commented out 'formatString' for gmail and uncommented the one for hotmail. However it doesn't direct me right. Also the one described [here]("http://ubuntuforums.org/showpost.php?p=3194752&postcount=28") doesn't do it for me. I tried clicking one the email-addresses in my contacts book which gives me this url:

```
http://bl135w.blu135.mail.live.com/mail/EditMessageLight.aspx?Mai\
lTo=%s&n=791832054
```

where %s is the email address. When I paste this one it works as far as the resulting page is concerned. The only peculiar thing is that the resulting url is something like this:

```
http://bl135w.blu135.mail.live.com/mail/EditMessageLight.aspx?MailTo=bogus@email.com&n=791832054http://bl135w.blu135.mail.live.com/mail/EditMessageLight.aspx?MailTo=&n=791832054http://bl135w.blu135.mail.live.com/mail/EditMessageLight.aspx?MailTo=&n=791832054http://bl135w.blu135.mail.live.com/mail/EditMessageLight.aspx?MailTo=&n=791832054http://bl135w.blu135.mail.live.com/mail/EditMessageLight.aspx?MailTo=&n=791832054
```

That is, the same thing five times!

So it basically works with the address, but when I try to add stuff like 'Subject' etc it ignores it, or just doesn't work at all. Does someone have any clue to how it should be? By the way, what the hell is this number 'n'? It seems to be different for each mail I begin. The only thing I'm sure about is that it doesn't work without it.

Any help is greatly appreciated!

---

### Post by ljungkvist on 2008-06-11
Ok, I'm sorry that I didn't try this before I wrote the last post. Now I've actually gotten it to work. Because I still have a Windows partition on my computer I tried click your links there and noticed the address it followed. With the following address it works perfectly:

```
http://hotmail.com/secure/start?action=compose&to=%s&subject=%s&body=%s&cc=%s&bcc=%s
```

I hope at that someone else will benefit from this aswell.

---

### Post by mssever on 2008-06-11
> **ljungkvist said:**
> Ok, I'm sorry that I didn't try this before I wrote the last post. Now I've actually gotten it to work. Because I still have a Windows partition on my computer I tried click your links there and noticed the address it followed. With the following address it works perfectly:

```
http://hotmail.com/secure/start?action=compose&to=%s&subject=%s&body=%s&cc=%s&bcc=%s
```I hope at that someone else will benefit from this aswell.
Thanks for providing this. I've posted an updated version in first post that includes your corrected format string. This has been a long standing bug, and I'm glad to see it fixed.

---

### Post by cpetercarter on 2008-06-11
It is possible to configure Firefox 3 so that gmail is the default application for "mailto" links. The procedure is very straightforward -- took me about 3 minutes.

See [http://lifehacker.com/392287/set-firefox-3-to-launch-gmail-for-mailto-links]("http://lifehacker.com/392287/set-firefox-3-to-launch-gmail-for-mailto-links")

---

### Post by mungerd on 2008-06-25
Nicely done!

For Gnome users wanting to use their Gnome-configured browser, I would suggest replacing
```
browser='firefox'
```
with
```
browser=`gconftool-2 --get '/desktop/gnome/url-handlers/http/command' | cut -d' ' -f1`
```
in the gmail_link script, instead of using the gmail_link_select_browser utility.

---

### Post by mssever on 2008-07-01
> **mungerd said:**
> Nicely done!

For Gnome users wanting to use their Gnome-configured browser, I would suggest replacing
```
browser='firefox'
```with
```
browser=`gconftool-2 --get '/desktop/gnome/url-handlers/http/command' | cut -d' ' -f1`
```in the gmail_link script, instead of using the gmail_link_select_browser utility.
Nice suggestion. Do you know how to detect whether or not Gnome is currently in use? If so, then gmail_link should do this automatically if Gnome is in use, and fall back to a default otherwise.

---

