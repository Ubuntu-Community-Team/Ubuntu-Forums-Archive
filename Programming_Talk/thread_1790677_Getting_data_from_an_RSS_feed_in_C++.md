---
title: "Getting data from an RSS feed in C++"
date: 2011-06-25
forum: Programming Talk
---

### Post by faillord adam on 2011-06-25
Is there a way to access data from an RSS feed in C++? I'm a bit of a C++ noob.

---

### Post by cgroza on 2011-06-25
You need to fetch it with some library such as libcurl and then parse it.
I am not familiar with RSS feeds and I do not know what is the underlying format.

EDIT: The format is just plain xml. You can use a library such as rapidxml to parse the fetched xml stream.

---

