---
title: "Bluebuntu... a Bluefish question"
date: 2012-07-30
forum: Programming Talk
---

### Post by EightsAndAces on 2012-07-30
I know this is not directly a Ubuntu question, but sort of...

I'm migrating to Ubuntu from Windows. So far, I really like the Linux/Ubuntu environment and community. I'm wishing I'd done it years ago. 

My quandary this morning is how to get to server files in Bluefish once you've screwed up your password. I have 4 ftp accounts that all use the same host. I set an improper password under Bluefish's Open URL user ID (at least I think that's what I did) and had the "remember forever" checked. Now it never prompts me for a user or password; it just gives me a red tab with the host name (fails to connect). Bluefish Open URL does work as expected on a different Ubuntu computer.

So, How can I find the Bluefish file that contains URL information and edit it? Or, How can I reset an Open URL password in Bluefish? Or, How can you use a different user ID for the same host once you've saved one ID as remember forever (it apparently does just that)?

Pardon the elementary question but I spent 2 hours trying to answer any one of the 3 questions above.

---

### Post by EightsAndAces on 2012-08-01
Ok since no one has been able to solve this riddle, I'll give my own novice answer to my novice question now that I've spent quite a bit of time finding it...

Bluefish apparently does not store URL passwords in a file; there is no file to edit; the problem had nothing to do with Bluefish. The password for the URL is stored by Seahorse Passwords and Keys utility. Open the Passwords and Keys utility, find and delete the entry for the erroneous URL under the passwords tab, and close Passwords and Keys. Bluefish then prompts you for the ID and password when opening the URL.

Still unanswered: How can you use a different user ID for the same host once you've saved one ID as remember forever?

I have 3 websites on one server. I have a FTP account for each and one master account with server "root" access. They all use the same host name. If you save a "remember forever" ID for a host, then you never get the option to change that when you call that host under open URL. Apparently, not an option or possibility, but, I can live with that.

---

