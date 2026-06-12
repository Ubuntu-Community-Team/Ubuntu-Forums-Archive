---
title: "Using import command on switched user"
date: 2010-09-12
forum: Programming Talk
---

### Post by KingNeil on 2010-09-12
I've been using the ["import"]("http://linux.about.com/library/cmd/blcmdl1_import.htm") command to take screenshots. 

I have a 2-user system set up. Both would be logged in at the same time. One of the users needs to use the import command. This user would be switched away from, while the other is actively being used.

When I run "import" with the user switched to, it works fine. When the user is switched away from, it takes a screenshot of a black screen.

I can understand why: because I guess X server isn't processing the switched user's graphics. But, is there a way to make it do so?

---

