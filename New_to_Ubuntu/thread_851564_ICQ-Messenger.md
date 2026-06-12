---
title: "ICQ-Messenger"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Vossibear on 2008-07-06
Hi

I am searching for an ICQ Messenger like miranda.

I do not want to use pidgin. I want a messenger, which is stable and which have a pluginoption with good plugins like miranda.

Do you have one?

:) Vossibear

---

### Post by EXCiD3 on 2008-07-06
Licq might be something worth checking out. What do you have against pidgin?

---

### Post by lkajdflkjaoeif on 2008-07-06
I can recommend Bitlbee. It allows you to contact your AIM/ICQ/MSN/Jabber contacts by connecting to its server using the IRC protocol. That means you can use any IRC client. I like irssi best but you can also use Xchat if you prefer GTK based applications.

Regards,
lkajdflkjaoeif

---

### Post by Vossibear on 2008-07-06
I want a simple style und I had problems with pidgin ... it does not like my girlfriend ;) I didn't saw her.

So I want another ... and a normal ICQ Messenger and not something over IRC or something else but thx for your trials

---

### Post by Vossibear on 2008-07-06
So I have installed Licq ... and there is an error when I want to go online with my ICQ account.

[ERR] Unknown sign on error: 0x1C

Do you know the problem?

---

### Post by lkajdflkjaoeif on 2008-07-06
> **Vossibear said:**
> I want a simple style und I had problems with pidgin ... it does not like my girlfriend ;) I didn't saw her.
Pidgin does not like your girlfriend? How do you know? Which problems did you have? My mother is also using Pidgin without any problems (but using Jabber).

> So I want another ... and a normal ICQ Messenger and not something over IRC or something else but thx for your trials
Please define "normal". You could also take a look at Gajim, CenterIM (it's a fork of the previously mentioned Centericq) and Finch which is a console version of Pidgin. I do not recommend Finch as it is very buggy and uses nearly the same dialogs as Pidgin which does not make sense on a console.

Edit: Gajim is a Jabber/XMPP messenger. So you have to use ICQ transports.

---

### Post by lkajdflkjaoeif on 2008-07-06
> **Vossibear said:**
> So I have installed Licq ... and there is an error when I want to go online with my ICQ account.

[ERR] Unknown sign on error: 0x1C

Do you know the problem?

It's a bug. This has already been fixed in the development version. See [http://bugs.gentoo.org/show_bug.cgi?id=230387](http://bugs.gentoo.org/show_bug.cgi?id=230387).

---

### Post by EXCiD3 on 2008-07-06
You could also try Kopete

---

### Post by lkajdflkjaoeif on 2008-07-06
You could also give ysmICQ, Sim-IM and GnomeICU a try.

---

### Post by Vossibear on 2008-07-06
I found that fix too, but I dont understand what I have to do on this page and how I have to install it ...

The Problem with pidgin:

At fist I cant see the real online status of her. Pidgin shows me that he is offline all the time. And then I wasnt able to write her messages ... but it was before I have installed ubuntu new. So I want to trie the fix for LICQ and pidgin.

THX

---

### Post by lkajdflkjaoeif on 2008-07-06
> **Vossibear said:**
> I found that fix too, but I dont understand what I have to do on this page and how I have to install it ...
You need to compile Licq and patch the file that contains the bug. Have you also tried CenterIM?

> At fist I cant see the real online status of her. Pidgin shows me that he is offline all the time. And then I wasnt able to write her messages ... but it was before I have installed ubuntu new.
Perhaps she is invisible? Try another account and her UIN. If it's not working, open a bugreport.

> So I want to trie the fix for LICQ and pidgin.
That's confusing. The fix for Licq has nothing to do with Pidgin. Just compile Licq from source. Be sure you're using the latest snapshot which already includes this bugfix.

---

