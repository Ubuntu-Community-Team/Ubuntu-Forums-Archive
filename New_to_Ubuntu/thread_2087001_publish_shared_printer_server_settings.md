---
title: "publish shared printer server settings"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by gscratch on 2012-11-22
I apologise if this has been answered; a search did not find it.  I want to share a printer from Ubuntu 12.04 LTS to Windows machines

I have installed the printer, I can print to it correctly from the Ubuntu machine.  In System Settings, I right-click the printer and share it.  From a windows machine on the network I can see the shared-out printer.  When I try to install the printer on that Windows machine, I get a permissions error

back in Ubuntu -> System Settings -> printer, when I un-share and then share the printer, the message is : "Shared printers are not available to other people unless the 'publish shared printers' option is enabled in the server settings"  and in the printer's properties is "Not published.  See server settings"

so my question is:  what settings in what server?  I find nothing in System Settings, or in a search of the Ubuntu desktop help, or of this forum

thanks.
Glen

---

### Post by gscratch on 2012-12-01
no replies in a week?
Do you need more information?
thanks,

---

### Post by critin on 2012-12-01
> **gscratch said:**
> no replies in a week?
Do you need more information?
thanks,

I couldn't ever get my Lexmark to work between win and ubuntu, but I read that certain printers have problems.    It can be seen, but wouldn't allow printing so I gave up.  Some brands work instantly, others don't.

I assume you've permitted sharing on ALL networks in Windows?

---

### Post by gscratch on 2012-12-01
Never mind; I found it.

however, I get a permissions error from the client, so I'll have to work on that.  likely it's the user that I'm logged into the client as.

---

### Post by kgr132 on 2012-12-10
-EDIT-
I forgot, with the Global Menu a lot of things fade into the background. If you open up "Printers", a window appears showing any connected printers. Right clicking the printer to get its properties will show that it's not published. If you Cancel that and move your mouse to the top of the screen, the Printing menu will appear and Server is a choice. Clicking "Server" allows you to edit settings that will Publish your printer. It's a bit frustrating to have to revisit this, since my printer was "published" just fine for the past year. Apparently the upgrade from 11.10 to 12.10 "unpublished" it.

---

