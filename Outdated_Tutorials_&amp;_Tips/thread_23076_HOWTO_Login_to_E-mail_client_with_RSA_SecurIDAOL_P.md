---
title: "HOWTO: Login to E-mail client with RSA SecurID/AOL Passcode"
date: 2005-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Cybermagellan on 2005-03-31
Q: Are there any E-mail applications that allow for SecurID/AOL Passcode logins?

A: Short answer: No - Long answer: Yes

**What?**
America Online, Inc. as well as other companies use a device called a SecurID to allow another method of security while logging into E-mail and other sensitive sites. The technology works by synching the device with a server and issuing the user a "tag" that changes numbers randomly built around an algorithim that the server and tag are both branded to for that account. Once the user logs in with their regular username and password then they are presented with a screen which allows them to enter the number from the tag which synch's with the server allowing completion of the log-in process. More information can be found on the RSA Website.

**How**
OK, so the question is how do we do this? Simple but no one spells it out. Follow these steps to sign in with your SecurID/Passcode

1. In your E-mail software (Evolution and/or Thunderbird) create your account with the mail servers as incomming and outgoing as directed by your service

For AOL: 
Incomming Mail=imap.aol.com
Outgoing Mail=smtp.aol.com

2. Go through the standard setup **EXCEPT** when you get to the part where it says to "use secure connection (SSL)" make sure that is checked.

3. Follow account preferences to completion and finish.

4. When presented with the screen requesting password information it needs to be entered in the following format 
**[CENTER]PASSWORD/TAGNUMBERS[/CENTER]** 

5. Do **NOT** click to save the password...the tags number changes every 60 seconds so the next time you log-in the old SecurID login will change and give you "Invalid SecurID: Please enter a valid SecurID"

**Why?**
I know alot of people are asking well if this is a big AOL thing...and AOL doesn't make software for Linux WHY would anyone do this?
[list=1]
[*]AOL has open mail access now. What is to stop people from comming to linux now?
[*]AOL isn't the only company that uses the SecurID
[/list] 

HTH

Shawn

---

### Post by Jakanden on 2006-09-16
Hello,

I was googling for AOL and SecurID issues and I was wondering if there was anything to keep it from timing out? After about 1-2 hours when I click "Get mail" I have to re-authenticate even though TB is checking email every 5 minutes.

The same goes for outgoing server although that timeout seems to be even shorter.

---

