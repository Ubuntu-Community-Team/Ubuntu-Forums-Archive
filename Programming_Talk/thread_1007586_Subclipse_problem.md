---
title: "Subclipse problem"
date: 2008-12-10
forum: Programming Talk
---

### Post by men8th on 2008-12-10
Hi all,

Please excuse me if this is the wrong forum for this kind of question...

I've just (a couple of evenings ago) installed Ubuntu 8.10, Eclipse, SVN and Subclipse. My problem is getting Subclipse to behave properly. I'm pretty new to this (some Unix experience a couple of years ago) so sorry if my question has an obvious answer.

I've setup a new SVN repository:
```

svnadmin create /home/tim/svn/repos

```

Linked to it in Eclipse:
[LIST]
[*]Go to Subclipse perspective
[*]Add SVN repository
[*]URL: file:///home/tim/svn/repos
[/LIST]

Created a new Eclipse project and done my initial check in. All OK up to here. Now, when I chance one of the source files and attempt to check it into the repository I get the following error:

An internal error occured during: "SVN Commit"

How do I go about fixing this. I am running the latest versions of Eclipse/Subclipse/SVN. If I issue commands from the command line then I can commit fine, just not through the GUI.

I've been battling with this for a couple of evenings now, can't seem to google any info. Any suggestions greatfully recieved. Tim

---

### Post by tinny on 2008-12-10
If you have the "Console" window open when you try and commit do you get any extra debug type info?


Also what SVN client is Eclipse using?


Window > Preferences > Team > SVN

"SVN interface" (What is selected?)

---

### Post by men8th on 2008-12-11
Hi tinny, thanks for the reply.

There is no debug info in the consol. However...

When I went to the preferences window for a moment I couldn't see what you were on about, then I realised that the window could be enlarged downwards revealing more options. The client is listed as "JavaHL (JNI) Not Available". Presumably this is the problem and I need to download/install it from somewhere.

---

### Post by tinny on 2008-12-11
> **men8th said:**
> Hi tinny, thanks for the reply.

There is no debug info in the consol. However...

When I went to the preferences window for a moment I couldn't see what you were on about, then I realised that the window could be enlarged downwards revealing more options. The client is listed as "JavaHL (JNI) Not Available". Presumably this is the problem and I need to download/install it from somewhere.

I generally use the SVNKit option.

---

