---
title: "Hyperlinks in email"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by cmcfarland21 on 2008-04-28
In Evolution mail, Nothing happens when I click on a link in the email.   The browser (Firefox) doesn't open if closed nor does the browser open the link if the browser is already opened.  I have to copy and paste.  Anyone know why?

---

### Post by 1richard on 2008-05-13
This is what I did and it works   
   1. Open Thunderbird version 2.0.0.14
   2. Go to the Edit menu
   3. Click on Preferences
   4. Click the Advanced tab
   5. Click the Config Editor button.
   6. An about:config window will open up.
   7. In the Filter box, enter network.protocol-handler.app.http
   8. If the editor is unable to locate it, create a new string and input network.protocol-handler.app.http.
   9. Enter firefox for the string value.
  10. Close out and restart Thunderbird.

Hyperlinks should now be available in your email!

---

### Post by freesitebuilder on 2008-05-13
But s/he isn't using TB, he's using Evolution. :)

Do the links show as normal - as they do in your web browser? If you right-click, do you get the load in browser/copy to clipboard options? I can't see anything in prefs to change browser. I've never had this problem with Evo - have you looked in Launchpad?

---

### Post by thabo on 2008-05-15
> **cmcfarland21 said:**
> In Evolution mail, Nothing happens when I click on a link in the email.   The browser (Firefox) doesn't open if closed nor does the browser open the link if the browser is already opened.  I have to copy and paste.  Anyone know why?

Im getting exactly the same probelm. Everything else under Evolution is working fine. Rightclick gives me the option for opening but nothing happens.

---

### Post by stchman on 2008-05-15
> **cmcfarland21 said:**
> In Evolution mail, Nothing happens when I click on a link in the email.   The browser (Firefox) doesn't open if closed nor does the browser open the link if the browser is already opened.  I have to copy and paste.  Anyone know why?

It should when I click a hyperlink in Evolution it opens FF3 or creates a new tab in FF3.

---

### Post by freesitebuilder on 2008-05-16
I can't find anything in Launchpad for this, bugzilla isn't loading for me at the moment. The mailing list only had two entries for links, and they were back in 2002/2003. You could try the mailing list, or the irc, or add it as a bug to Launchpad.

I've got no problems, I'm using Fx3, Hardy (8.04) and Evo 2.22.1 - what  are you using?

---

### Post by cmcfarland21 on 2008-05-23
I had FF3 and un-installed it and installed FF2.  SOmehow Evolution is linking to FF3 which I know longer have./  Anyway to switch the default browser in Evolution?

---

### Post by ruru on 2008-06-11
I have this same problem - I need FF2 because of the Zotero plugin. 
Does anyone know how to change Evolution's default browser?

---

### Post by ruru on 2008-06-11
OK - just solved this.

[http://ubuntuforums.org/showthread.php?t=796154&highlight=evolution+browser+open]("http://ubuntuforums.org/showthread.php?t=796154&highlight=evolution+browser+open")

has the answer. The global prefs are set to open FF3 'firefox'.

Changing System > Preferences > Preferred Applications default browser to:

> firefox-2 %s

has the desired effect.

---

### Post by hyper_ch on 2008-06-11
> **ruru said:**
> I need FF2 because of the Zotero plugin.

Nightligh Building Tools addon helps here ;)

---

### Post by sybille on 2008-06-12
> **ruru said:**
> I have this same problem - I need FF2 because of the Zotero plugin.

Zotero is now compatible with Firefox 3. More details here: [http://www.zotero.org/blog/zotero-104-launches/](http://www.zotero.org/blog/zotero-104-launches/)

---

