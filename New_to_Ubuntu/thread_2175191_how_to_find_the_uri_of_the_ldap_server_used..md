---
title: "how to find the uri of the ldap server used."
date: 2013-09-18
forum: New to Ubuntu
---

### Post by Zombir on 2013-09-18
Hi,
I'm a total noob to this networking issue but am suppose to find the uri of the ldap server wer're using. (I think its supposed to be something like ldaps:\\....) and have no clue how to do this. All I know is that we're using some smbldap something. We're using xubuntu as the os for client computers. Is there anyway that I could find the uri of the ldap that I've got authentication from ? Sorry that's all I know and our network maintenance guy is ill. I've been searching in the internet for hours now and nothing is making sense to me. Please help. 
Sorry for the noob question.

---

### Post by sandyd on 2013-09-18
Depends on what ldap setup your using.

Ill take a wild guess, and say your using libpam-ldapd
should be somewhere in /etc/nslcd.conf

---

