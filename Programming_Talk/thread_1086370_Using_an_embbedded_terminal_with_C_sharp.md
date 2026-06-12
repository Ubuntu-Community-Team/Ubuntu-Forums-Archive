---
title: "Using an embbedded terminal with C sharp"
date: 2009-03-03
forum: Programming Talk
---

### Post by orlox on 2009-03-03
Hi! Im trying to embbed a terminal on a project Im making with monodevelop,But I cant seem to get it right.

There are vte bindings for C sharp and after looking I found some documentation for it:

[http://www.go-mono.com/docs/index.aspx?link=N:Vte]("http://www.go-mono.com/docs/index.aspx?link=N:Vte")

There is an example there also.

The thing is, I dont know how to accept the lines "using Gnome;" and "using Vte;", monodevelop gives me the following errors:

```

Description=The type or namespace name `Gnome' could not be found. Are you missing a using directive or an assembly reference?
Description=The type or namespace name `Vte' could not be found. Are you missing a using directive or an assembly reference?

```

Somewhere I read that I needed to install vte-sharp to use vte. Looking with synaptic I installed libvte0.16-cil that where stated as the CLI bindings for vte and gnome-desktop-sharp2 that where stated as the CLI bindings for the gnome desktop environment. But this didnt solve the problem.

I believe I should do something in monodevelop so the compiler knows of the presence of the vte and gnome bindings, but im not very sure what...

---

### Post by orlox on 2009-03-04
Well, it was nothing more than a monodevelop newbie problem :P

I only needed to add the references and add vte-sharp and gnomedesktop-sharp.

---

### Post by directhex on 2009-03-04
What's your project? I'm curious about anything using VTE#

---

### Post by orlox on 2009-03-04
Im thinking in developing a system to view and edit howtos (intended for system customization or fixes). The idea is to create an xml specification to define steps, commands to be run, files to be edited, etc... and then implement a viewer and an editor for this.

The idea of the vte is to run commands specified in the howto directly in an embbedded terminal.

---

### Post by directhex on 2009-03-04
> **orlox said:**
> Im thinking in developing a system to view and edit howtos (intended for system customization or fixes). The idea is to create an xml specification to define steps, commands to be run, files to be edited, etc... and then implement a viewer and an editor for this.

The idea of the vte is to run commands specified in the howto directly in an embbedded terminal.

Interesting idea

---

