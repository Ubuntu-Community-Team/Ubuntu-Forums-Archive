---
title: "Postfix Antivirus Exclusions"
date: 2023-02-01
forum: New to Ubuntu
---

### Post by rovied01 on 2023-02-01
What Postfix directories or files we should exempt or not to scan by Ubutntu OS antivirus like Kaspersky in our case?

---

### Post by SeijiSensei on 2023-02-01
You're not going to get any viruses in the Postfix installation itself. I'd scan /var/spool/mail where the inboxes are stored and the users' home directories.

---

### Post by mIk3_08 on 2023-02-01
In my case, I don't use antivirus in Linux Ubuntu. I think shield or Livepatch is enough. Regards and cheers.

---

### Post by ActionParsnip on 2023-02-02
/etc/postfix is where the configs live but as SeijiSensei states, you won't get issues here. You want to scan the storage folders for the email more.

---

### Post by rovied01 on 2023-02-07
Thanks for the information provided by all, but we more interested to know the directories and the files which we don't have to scan by the Antivirus. I think below file and directories are the correct one. Please confirm. Kindly note this is just a Relay Gateway server, there is no users' mailboxes in Postfix.

1- [COLOR=#4D5156][FONT=arial] /etc/[/FONT][/COLOR][COLOR=#5F6368][FONT=arial]**postfix**[/FONT][/COLOR][COLOR=#4D5156][FONT=arial]/main.cf          (Configuration File)
2-  [/FONT][/COLOR][COLOR=#4D5156][FONT=arial]/var/spool/[/FONT][/COLOR][COLOR=#5F6368][FONT=arial]**postfix**[/FONT][/COLOR][COLOR=#4D5156][FONT=arial]/            (Message Queue)
[/FONT][/COLOR][COLOR=#4D5156][FONT=arial]3- /var/logs/mail/                    (Logs)

[/FONT][/COLOR]

---

### Post by ActionParsnip on 2023-02-07
You WILL want to scan the message queue. That is where the emails come in. You will protect your clients by scanning there

---

### Post by rovied01 on 2023-02-07
Antivirus scanning can corrupt the messages or configuration. To safe the server from corruption, there must be some files or directories that shouldn't be can by AV. Like we configure AV Exclusions or Exception in MS Exchange and Lotus Domino Servers. Likewise, I want to configure AV exclusion in Postfix.

---

