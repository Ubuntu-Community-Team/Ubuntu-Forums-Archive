---
title: "LIbreOffice stopped saving files"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by Snapcase on 2013-02-05
It worked fine until yesterday but today I cannot save documents anymore. Something related to permissions. I tried changing my Documets folder permissions in Properties but nothing changed. What can I do?

Thanks.

---

### Post by Filipek on 2013-02-05
> **Snapcase said:**
> It worked fine until yesterday but today I cannot save documents anymore. Something related to permissions. I tried changing my Documets folder permissions in Properties but nothing changed. What can I do?

Thanks.


Snapcase,

I am afraid you are going to have to share a bit more on that topic. 

[LIST=1]
[*]how do you start your LibreOffice?
[*]has anything changed with your computer/file system recently?
[*]are you logging in as the same user as before?
[*]what does it say when the document could NOT be stored? would you please share a screenshot for example?
[/LIST]

Please, let us know so we can help.

---

### Post by Snapcase on 2013-02-05
1- just click on the Writer icon in the panel
2- Not as far as I'm aware. Haven't installed anything in days.
3- Yes. always the same user.
4- It says nothing actually. I just quits when hitting save. Then when reopening the Writer it asks to recover the documents. Accept and the documents are just empty.

---

### Post by Filipek on 2013-02-05
Hmm, since it quits upon hitting Save button it seems it is some problem within the LibreOffice software itself :-(

One last option that comes to my mind before pointing you to LibreOffice bugs section is to start the Writer from within the Terminal (from the command line).

And when it fails (quits), take a look on that terminal window what does that say - or try to post it here. Maybe it will ring some bell.

Without any error, it could be just about anything :confused:

---

### Post by Snapcase on 2013-02-05
There we go.

```
paco@paco:~$ libreoffice writer &
[1] 14028
paco@paco:~$ Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
Fontconfig warning: "/usr/lib/libreoffice/share/fonts/truetype/fc_local.conf", line 13: Having multiple <family> in <alias> isn't supported and may not works as expected
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode: 42 (X_SetInputFocus)
  Resource id:  0x540016c
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode: 42 (X_SetInputFocus)
  Resource id:  0x540016c
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode: 42 (X_SetInputFocus)
  Resource id:  0x5400ad4
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode: 42 (X_SetInputFocus)
  Resource id:  0x5400ad4

```

Also when launching this time popped up a window telling that the /paco/writer folder doesn't exist. (paco is obviously my user name).

And when hitting save as into my Documenta folder (or any other else) I get this other pop up:

> Error saving the document Untitled 1:
Object not accessible.
The object cannot be accessed due to insufficient user rights.

---

### Post by Snapcase on 2013-02-05
Duplicated fonts? Why?

---

### Post by Snapcase on 2013-02-05
This is the fc_local.conf file:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "/etc/fonts/conf.d/fonts.dtd">
<fontconfig>

	<!-- Alias similar/metric-compatible families from various sources: -->

	<alias binding="same">
	  <family>Liberation Sans Narrow</family>
	  <family>Arial Narrow</family>
	  <default>
	  <family>Arial Narrow</family>
	  </default>
	</alias>

<!-- -->
	<alias binding="same">
	  <family>Arial Narrow</family>
	  <accept>
	  <family>Liberation Sans Narrow</family>
	  </accept>
	</alias>
<!-- -->

</fontconfig>
```

What's wrong with it?

---

### Post by Snapcase on 2013-02-05
And this is the 50-user.conf file:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<!-- Load per-user customization file -->
	<include ignore_missing="yes" prefix="xdg">fontconfig/conf.d</include>
	<include ignore_missing="yes" prefix="xdg">fontconfig/fonts.conf</include>
	<!-- the following elements will be removed in the future -->
	<include ignore_missing="yes" deprecated="yes">~/.fonts.conf.d</include>
	<include ignore_missing="yes" deprecated="yes">~/.fonts.conf</include>
</fontconfig>
```

---

### Post by grahammechanical on 2013-02-05
May I say something? I am on 12.04 with Libreoffice 3.5. If I run

```
libreoffice writer
```

I also get the error message /home/graham/writer does not exist. So, that error message is nothing to do with the problem. Try

```
libreoffice
```

that works and I do not get any error messages. Do you? Also, when you open up Writer go to tools/options/paths. What is the path to My Documents? Is it the correct one? In other words is Writer trying to save into a location/folder that does not exist?

On my 12.04 it is /home/graham/Documents/Documents. I have other installs of Ubuntu (13.04) and I think that the path is different in that Libreoffice. Find out if Libreoffice is trying to Save into a folder that does not exist.

Regards.

---

### Post by Snapcase on 2013-02-05
Tried launchuing Libreoffice instead of the writer and the same configuration errors were reported. Anyway. I was able to save documents, but only in the Documents folder (???!!!) Why not in any other folders?

BTW, This is the path targeted in the Paths options... 

Anyway, this behavior bugs me. I want to save documents inside the folders I'm working in.

---

### Post by kurt18947 on 2013-02-05
I just tried creating a simple two sentence .odt file and saving it in my 'pictures' folder.  It saved and opened correctly.  I'm using  12.10 gnome remix and L.O. 3.6.6.2.2 Build I.D. 360m1(build:2)).   Just to check for config problems, could you create another user account and try to reproduce the misbehavior in that account?  If you're trying to save to user created folders, I'd wonder about folder permissions.

---

### Post by Snapcase on 2013-02-05
No way. Just into the Documents folder.

Wait. now not even in de Docs folder.

Gonna try a different user.

---

### Post by Snapcase on 2013-02-05
It works perfectly well in a different user account. Permissions issues as expected...

What can I do now?

---

### Post by kurt18947 on 2013-02-05
> **Snapcase said:**
> It works perfectly well in a different user account. Permissions issues as expected...

What can I do now?

I'm am certainly no expert.  It's good news that creating a new user account fixed your problem.  I think that means the problem lies somewhere in the problem user's home folder.  I poked around my /home folder and found this:

/home/.config/libreoffice/3/user

There are 15 folders plus one .xcu file.  I would probably backup any data files in the /home directory before doing much else.  I know in firefox I can delete the .config folder and firefox will create another on its next startup.  I don't know if LibreOffice would do the same or not.  You could experiment on your newly created user account that presumably contains nothing of value.  If Libreoffice totally pukes, delete the newly created account and no harm done.  

If LibreOffice will create a new folder,  you can backup any custom dictionaries and the like, delete to problem folder, let LO create a new config folder and restore your preferences.  if that doesn't work for whatever reason, would it be a huge hassle to create a new account,  move as much as possible from the old user account to a new user account and delete the old?  You wouldn't want to move the libreoffice configuration files, obviously.   You could also mess around with adding .old file name suffixes to suspect files then retry saving within the problem user account.  If that fixes your problem, you could delete the files with .old suffixes since they were recreated without the problematic content.  Again, I'm no expert but these are things I'd try in your situation.

This probably goes without saying but I'll say it anyway.  If you have any important data such as documents, photos, financial records, make _sure_ you have backups that you can read and restore.

---

### Post by Snapcase on 2013-02-05
Bingo!

I moved that registrymodifications.xcu file to a different directory and launched LibreOffice. It instantly created a new one and now it works as it should.

That's like in the old times when I was a ProTools user. You have to delete the preferences file from time to time when weird things start to happen. Lesson (re)learnt!

Thank you!

---

### Post by Snapcase on 2013-02-05
Damnit... it's back if I directly launch the writer.

---

### Post by Snapcase on 2013-02-05
It's not exactly that. It gets screwed up if I try to save anything in the Downloads folder. Then the permissions problems starts and from that point it's impossible to save anything anywhere. If I delete the registrymodifications.xcu file it gets solved. Then if I try to save anything in Downloads, all this mess starts again.

---

### Post by kurt18947 on 2013-02-06
> **Snapcase said:**
> It's not exactly that. It gets screwed up if I try to save anything in the Downloads folder. Then the permissions problems starts and from that point it's impossible to save anything anywhere. If I delete the registrymodifications.xcu file it gets solved. Then if I try to save anything in Downloads, all this mess starts again.

Hooo boy!  Maybe spend some time on LibreOffice.org -> get help?  If you save something in /Downloads from Firefox or another browser and that causes problems with LibreOffice, I would have no idea.  Would it be a huge PITA to delete that user account?  That's presuming a new account would not have the same issues.

Edit:  I had another thought though this may be an example of fools rushing where angels fear to tread :rolleyes:.  Delete the registrymodifications.xcu, open Libreoffice and let it recreate the file then close LibreOffice and immediatly change that file's permissions to read only.  I have NO clue if that'd work or not but to paraphrase Thomas Edison "I have not failed, I have only discovered yet another way that does not work.":P

---

