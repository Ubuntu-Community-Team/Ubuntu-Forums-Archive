---
title: "Trying to install KDE on Ubuntu"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by cygnis1 on 2008-07-07
I am trying to install Kde on my Ubuntu machine, and I believe it installed ok. However, in the terminal there is a postfix configuration screen, and I don't know how to deal with it.  Any help will be appreciated.  Here is the configuration screen:

 Please select the mail server configuration type that best meets your   &#8593; 
  &#9474; needs.                                                                  &#9646; 
  &#9474;                                                                         &#9618; 
  &#9474;  No configuration:                                                      &#9618; 
  &#9474;   Should be chosen to leave the current configuration unchanged.        &#9618; 
  &#9474;  Internet site:                                                         &#9618; 
  &#9474;   Mail is sent and received directly using SMTP.                        &#9618; 
  &#9474;  Internet with smarthost:                                               &#9618; 
  &#9474;   Mail is received directly using SMTP or by running a utility such     &#9618; 
  &#9474;   as fetchmail. Outgoing mail is sent using a smarthost.                &#9618; 
  &#9474;  Satellite system:                                                      &#9618; 
  &#9474;   All mail is sent to another machine, called a 'smarthost', for        &#9618; 
  &#9474; delivery.                                                               &#9618; 
  &#9474;  Local only:                                                            &#8595; 
  &#9474;                                                                           
  &#9474;                                 <Ok>

---

### Post by damis648 on 2008-07-07
When you installed KDE, did you use
```
sudo apt-get install kubuntu-desktop
```
or
```
sudo apt-get install kubuntu-kde4-desktop
```?
You must use one of these.

---

### Post by cygnis1 on 2008-07-07
I used this:  sudo aptitude update && sudo aptitude install kubuntu-desktop

---

