---
title: "MonoDevelop error"
date: 2006-09-13
forum: Programming Talk
---

### Post by profediego on 2006-09-13
Hi guys, 

I just installed Monodevelop and i am trying to use it, i open an example and got this error i think some libraries migth be missing but dont know wich ones do i have to install or what could somebody point me in the rigth direction please  Thanks

Erros:

[Task:File=/home/profediego/Projects/Borrenme/Borrenme/Main.cs, Line=3, Column=1, Type=Error, Description=The type or namespace name `Gtk' could not be found. Are you missing a using directive or an assembly reference?(CS0246)

[Task:File=/home/profediego/Projects/Borrenme/Borrenme/Main.cs, Line=4, Column=1, Type=Error, Description=The type or namespace name `Glade' could not be found. Are you missing a using directive or an assembly reference?(CS0246)

---

### Post by gmclachl on 2006-09-13
Did you install all the libraries you need?

 Off the top of my head you need gtk-sharp 

 apt-get install gtk-sharp or gtk-sharp2 

 When you open monodevelop and have your project open, right click references and make sure gtk is selected. 

 George

---

### Post by profediego on 2006-09-13
Thanks gmclachi, i knew i have to install something but didnt figure out what? 

Thanks a Lot

---

### Post by KnK9 on 2008-02-16
Thank you gmclachl, it worked for me !

But it starts only from the terminal and I have to be root. It says: 

(MonoDevelop:21125): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
1507 [-1226249328] INFO MonoDevelop.Core.ILoggingService (null) - Initializing service: MonoDevelop.Core.PropertyService
1638 [-1226249328] INFO MonoDevelop.Core.ILoggingService (null) - Initializing service: MonoDevelop.Core.SystemAssemblyService
2278 [-1226249328] DEBUG MonoDevelop.Core.ILoggingService (null) - Reading /root/.config/MonoDevelop/CodeCompletionData/mscorlib_2.0.0.0_b77a5c561934e089.pidb
2507 [-1226249328] DEBUG MonoDevelop.Core.ILoggingService (null) - Reading /root/.config/MonoDevelop/CodeCompletionData/mscorlib_2.0.0.0_b77a5c561934e089.pidb
3456 [-1226249328] INFO MonoDevelop.Core.ILoggingService (null) - Initializing service: MonoDevelop.Projects.Documentation.IDocumentationService

(MonoDevelop:21125): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
21471 [-1226249328] DEBUG MonoDevelop.Core.ILoggingService (null) - Writing /root/.config/MonoDevelop/CodeCompletionData/mscorlib_2.0.0.0_b77a5c561934e089.pidb


However it starts and works, but it's annoying I have to log as root. Do you have any idea?

Thanks

---

