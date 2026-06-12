---
title: "How to open a C# project in MonoDevelop?"
date: 2009-11-09
forum: Programming Talk
---

### Post by emigrant on 2009-11-09
hi all,
how to open a c# project in monodevelop?
the project just shown as a normal folder and not like a c# project :(

thank you very much for your help.

---

### Post by RaptorJesus on 2009-11-09
I assume that you are trying to open a Microsoft .Net project file, in that case you just have to create a Mono develop version by going File>New project.

---

### Post by emigrant on 2009-11-09
You mean i cant open what iv already created in visual studio?

---

### Post by directhex on 2009-11-09
> **emigrant said:**
> You mean i cant open what iv already created in visual studio?

No, RaptorJesus is wrong.

You should be able to open Visual Studio Solutions (.sln) and C# Projects (.csproj) from the File/Open menu. Generally, opening solutions works much much better than projects, since MD always needs a parent solution for any given project

---

### Post by RaptorJesus on 2009-11-10
Is this true, directhex? I always assumed that you had to create your own. I should probably stop offering suggestions on this forum.

---

### Post by directhex on 2009-11-10
> **RaptorJesus said:**
> Is this true, directhex? I always assumed that you had to create your own. I should probably stop offering suggestions on this forum.

MD is currently moving towards using VS project file formats instead of its own formats. It should be able to open ones produced by VS, but doesn't currently have a 100% success rate

---

