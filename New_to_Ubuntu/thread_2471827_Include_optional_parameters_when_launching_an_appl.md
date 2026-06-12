---
title: "Include optional parameters when launching an application"
date: 2022-02-10
forum: New to Ubuntu
---

### Post by plb2010 on 2022-02-10
I have an application (Reaper) that I have to launch from the command-line because there are several optional startup parameters that are required for my use of the app. Instead of typing out these parameters every time I launch the application, is there a way to append them to some file? so that when I click the application icon in the doc (or via ArcMenu) the parameters are automatically included?

I'm running Ubuntu 21.10.

Thanks...

---

### Post by Holger_Gehrke on 2022-02-10
The icons on the application overview are created from simple text files with the extension '.desktop' located either in /usr/share/applications - for applications visible and usable for all users - or in $HOME/.local/share/applications/ - for applications accessible only for a specific user. So either find the desktop file for Reaper (grep -i reaper /usr/share/applications/*) and change the line starting with 'Exec=' to include your options or copy that system wide file to $HOME/.local/share/applications/ and edit the copy to override the system file. Details on Desktop files can be found on [freedesktop.org]("https://specifications.freedesktop.org/desktop-entry-spec/latest/").

Holger

---

### Post by plb2010 on 2022-02-10
Great. Thank you. Solved!
P.

---

### Post by SeijiSensei on 2022-02-10
If you do launch the app from the command line, you could solve this problem by creating an alias for it:
```
alias myapp='app -a -b -c --long-option'
```
Then typing "myapp" will run the full command.

---

