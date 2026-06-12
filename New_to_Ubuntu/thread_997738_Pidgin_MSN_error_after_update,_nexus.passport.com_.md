---
title: "Pidgin MSN error after update, nexus.passport.com root certificate?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by DesiArnez6 on 2008-11-30
I have a similar problem to this, from the archives:
[http://ubuntuforums.org/showthread.php?t=706396](http://ubuntuforums.org/showthread.php?t=706396)

I have never had a problem until this morning after all the updates from update manager (I hadn't updated for a few weeks so there were probably about 40 files)

Anyways, I always connnet to Pidgin without problem, only this morning I couldn't login to my MSN account (Yahoo, AIM, and IRC were fine)

After I typed in my password for my msn account, I got this window:


_______________________________________________________________________
SSL Certificate Verification
-------------------------------

Accept certificate for nexus.passport.com?

The root certificate this one claims to be issued by is unknown to Pidgin.

[View Certificate...] [Reject] [Accept]

___________________________________________________________________________

*So, I clicked "View Certificate", and I got this window:


__________________________________________________________________

Common name: nexus.passport.com

Fingerprint (SHA1): ed:90:4f:86:8b:6b:3c:f0:89:37:60:23:40:ba:e9:c7:a1:2a:c2:1e

Activation date: Tue Jun 17 20:00:00 2008

Expiration date: Sun Jul 12 19:59:59 2009

_______________________________________________________________________



*So, I close that window, and decide to click to Reject, and I get this:

___________________________________________________________________
********(my sn)@hotmail.com (MSN) disconnected

Unable to authenticate: Unable to connect

Pidgin will not attempt to reconnect the account until you correct the error and re-enable the account.

[Close]
_______________________________________________________________________


Is this some sort of hack attempt, or corruted pidgin, or something?

I did notice an update package called gaim transition to pidgin or something when I did all these updates this morning from the update manager (But I've already had pidgin since I ugraded to Gutsy 7.10 a few months ago)

Any help will be appreciated.


So , what do I do? Any harm in accepting this "root certificate" whatever that means?

---

### Post by Hypo_Mix on 2008-11-30
i believe passport.com is MSN so you said decline MSN accessing pigin thereby shutting it out i think.

---

### Post by lametike on 2008-11-30
u may try amsn,quite good for msn accounts,sure better than the pidgin.
get it from its main website or [www.getdeb.net](www.getdeb.net)

---

### Post by kostkon on 2008-11-30
The certificate is valid. You need to accept it if you want to be able to connect to MSN.

---

### Post by doug-M on 2008-12-01
> **kostkon said:**
> The certificate is valid. 

You might tell them how to know the certificate is valid.It is too bad that Pidgin did such a poor job with this interface. But you are correct that certificate appears to be valid.

In any case you can't really properly validate the certificate with the interface they have provided. For some certificates such as the MSN one you can partially do it, for others such as google it is much harder.

So to partially validate the certificate look at the thumbprint they provided to you:
Fingerprint (SHA1): ed:90:4f:86:8b:6b:3c:f0:89:37:60:23:40:ba:e9:c7:a1 :2a:c2:1e

Now open a browser and go to the HTTPS (note the S) web site representing the common name: [https://nexus.passport.com](https://nexus.passport.com)

Double click on the lock icon in the bottom right corner of the browser, then select "View Certificate". The SHA1 Fingerprint listed should match the one that pidgin provided.

However if the browser gave you any warnings about not trusting the certificate then you shouldn't consider the certificate validated either. 

I would guess that the pidgin developers included their own list of trusted root certificate authorities and that doesn't include the one used by this particular certificate.

To properly validate certificates you (or the software) should really check:
- The Certificate was issued by a Certificate Authority (CA) that chains up to a root CA that you trust. Your browser or operating system comes with a list of CAs they have determined that you should trust.

- The certificate and the certificates of all CAs in the chain up to the issuing root CA has not been revoked. Normally this is done by checking the CRL (Certificate Revocation list), the location of which is embedded in the certificate.

- The Common Name and attributes of the certificate match the expected name and attributes. In the case of an SSL website the Common name should be the name of the web site (e.g.nexus.passport.com and [https://nexus.passport.com/](https://nexus.passport.com/) )

For more information try your fav search engine or perhaps:
Using Certificates
[http://www.mozilla.org/projects/security/pki/psm/help_20/using_certs_help.html](http://www.mozilla.org/projects/security/pki/psm/help_20/using_certs_help.html)

---

### Post by DesiArnez6 on 2008-12-01
Thanks for the info. I didn't much of any of that until now.

When I clicked on the page, "https://nexus.passport.com/"

I got:
"Windows Live ID Logo
 
The page is unavailable or no longer exists

The page you're trying to find is either temporarily unavailable or no longer exists.

Please do one of the following:

    * Click your browser's Refresh button to try reconnecting to the page.
    * Check the spelling of the web address in your browser's address bar.
    * Click your browser's Back button to go back to the previous page."

 Instead of a lock to click on.

 It is probably fine I suppose but sine I didn't understand certificates I wasn't sure. Once again, thanks for the info ;)

---

### Post by dalcom on 2008-12-08
He meant that when you try to view the https page, FireFox shows a lock in the status bar, not in the web page. Double click on that lock and you'll get the certificate info.
Other browsers do something similar, too.

---

### Post by bandito40 on 2008-12-12
I had the same problem and followed what doug-M had suggested and the certificates were different.  I tried accepting anyway it as I usually do but this time Pidgin didn't freeze and crash.  I checked the certificates under Tools option in the drop down menus and the was a certificate for nexus.passport.com.  I am now able to use Pidgin with msn again.  As for amsn, very nice but I like to able to see all of my contacts in one ims client.

---

### Post by horizons on 2008-12-16
Thanks for the great explanation doug-M.
That gave me peace of mind :D and it worked for me as well.

---

