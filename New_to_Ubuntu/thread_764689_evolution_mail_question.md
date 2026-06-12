---
title: "evolution mail question"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by lunaluna on 2008-04-24
can i set evolution every time i send something from my inbox to deleted happen the same time to webmail?

---

### Post by Canis familiaris on 2008-04-24
> **lunaluna said:**
> can i set evolution every time i send something from my inbox to deleted happen the same time to webmail?

Can you rephrase your question. I cannot understand it.

---

### Post by rouge568 on 2008-04-24
What she is saying is that she wants to be able to delete a message in her client software and have that message automatically deleted on the online client. 
E.g. Ah! I have spam! Let me delete it. Now let me go to a different computer and check my mail again through a web browser. Oh! I'm so glad I deleted that spam on my own computer and had it automatically deleted here. Now my clutter is way down!

I don't know the answer (I use thunderbird), but this should clarify the question.

---

### Post by warbread on 2008-04-24
The answer is IMAP.  Your webmail server must support this, and they should have more instructions on their site.  I used Thunderbird and Gmail, and this works perfectly.

---

### Post by hellomoto on 2008-04-24
i use izymail, they retrieve all my mail from hotmail which doesnt allow POp3 by default and then it automaticly removes the mail from the hotmail server too.

---

### Post by rplantz on 2008-04-26
> **lunaluna said:**
> can i set evolution every time i send something from my inbox to deleted happen the same time to webmail?

I think what you need to do is to open your "Trash" folder, then use Folder -> Expunge. You might have several Trash folders, but you should be able to tell where your "deleted" mail is going.

I have two imap accounts and did not realize for some time that I needed to do this additional step in order to delete the mail from the server.

---

### Post by Fedz on 2008-04-26
In Evolution > Edit Preferences > mail preferences > general (tab) > delete mail

x the option for 'empty trash folder on exit (every time)'.

Otherwise just highlight trash folder > right click and empty trash - this will delete, deleted mail from your inbox :)

Hope this helps :)

---

