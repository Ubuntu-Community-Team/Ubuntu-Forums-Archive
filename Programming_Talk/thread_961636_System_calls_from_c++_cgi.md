---
title: "System calls from c++ cgi"
date: 2008-10-28
forum: Programming Talk
---

### Post by bassMonkey on 2008-10-28
Hi,

I'm working on a school project that basically involves implementing a system similar to Java Server Pages in C++. We're not that far along yet but I'm trying to figure out how the dynamic building could work (basically just calling g++ to compile the generated code and running it). It's somewhat working atm but only when running from a shell, that's why I think it has something to do with permissions. 

I can't even call system("touch /tmp/test"), well I can - but it returns 256 and nothing happens. /tmp/ has drwxrwxrwt permissions btw - that's what I don't understand... Does apache somehow block cgi-scripts from executing system calls? Is there some clever way I haven't tought of to do this?

Thanks in advance! :)

---

