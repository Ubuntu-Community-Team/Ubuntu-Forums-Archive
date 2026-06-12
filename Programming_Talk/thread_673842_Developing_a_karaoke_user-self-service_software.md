---
title: "Developing a karaoke user-self-service software"
date: 2008-01-21
forum: Programming Talk
---

### Post by lian1238 on 2008-01-21
Hi,
I would like to create a GUI software for a karaoke service provider. The computer that runs this software will be operated by the user(s) alone with no staff present. The program will be used only with a mouse. Karaoke songs will be stored on the harddisk of the computer. Users must be able to browse the database and add songs to the playlist.

I would like to know which programming language(s) will be easiest to write this GUI program. The OS can be either linux or windows. Right now, I can only program (not so expertly, yet) in C++ but not GUI programs.

Please give me some tips on how to write this program. (languages to learn, libraries to use, etc.)

---

### Post by pmasiar on 2008-01-21
Because you do not need speed of C++, IMHO  you can finish this program faster in Python (including learning Python, which should not take more than couple of weeks max). See wiki in my sig for links.

wxPython is one of the most popular GUI toolkits.

SQLite is excellent simple embedded database library, you can run it without running a server.

Good luck!

---

### Post by lian1238 on 2008-01-21
Thanks for your reply.
What would be a suitable video format for such a database? One that would have a small filesize but still look good on a television monitor. The original resolution of a standard video has a height of around 240 ~ 290 px. Aspect ratio of 4:3.

Also, do I really need a database like SQLite at all?
I would like to use something like what rhythmbox uses. Able to import folders and files from harddisk. Does it use SQLite?

---

