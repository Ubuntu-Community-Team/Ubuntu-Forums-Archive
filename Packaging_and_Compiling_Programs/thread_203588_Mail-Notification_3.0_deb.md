---
title: "Mail-Notification 3.0 deb"
date: 2006-06-25
forum: Packaging and Compiling Programs
---

### Post by SpEcIeS on 2006-06-25
This morning I was trying to build a deb for the latest mail-notification, 3.0, however it errors out. The odd thing is when I compile manually, ./configure;make, everything works.

Now I guess what I am asking is, what file do I need to alter to allow the same configuration and compiling as the manual method. Realizing this sounds cryptic, I do not know how else to term it, but hopefully someone will know.

Here is the final ouput:
```
.libs/liborg_gnome_mail_notification_la-mn-evolution-plugin.o: In function `org_gnome_mail_notification_message_reading':/home/robb/build/mail-notification/mail-notification-3.0/src/mn-evolution-plugin.c:212: undefined reference to `mail_tools_folder_to_url'
.libs/liborg_gnome_mail_notification_la-mn-evolution-folder-tree-control.o: In function `mn_evolution_folder_tree_control_factory_cb':/home/robb/build/mail-notification/mail-notification-3.0/src/mn-evolution-folder-tree-control.c:76: undefined reference to `mail_component_peek'
:/home/robb/build/mail-notification/mail-notification-3.0/src/mn-evolution-folder-tree-control.c:76: undefined reference to `mail_component_peek_tree_model'
:/home/robb/build/mail-notification/mail-notification-3.0/src/mn-evolution-folder-tree-control.c:77: undefined reference to `em_folder_tree_new_with_model'
.libs/liborg_gnome_mail_notification_la-mn-evolution-folder-tree-control.o: In function `mn_evolution_folder_tree_control_get_property':/home/robb/build/mail-notification/mail-notification-3.0/src/mn-evolution-folder-tree-control.c:121: undefined reference to `em_folder_tree_get_selected_uri'
.libs/liborg_gnome_mail_notification_la-mn-evolution-folder-tree-control.o: In function `mn_evolution_folder_tree_control_set_property':/home/robb/build/mail-notification/mail-notification-3.0/src/mn-evolution-folder-tree-control.c:145: undefined reference to `em_folder_tree_set_selected'
.libs/liborg_gnome_mail_notification_la-mn-evolution-glue.o: In function `mn_evolution_glue_getUnseenMessages':/home/robb/build/mail-notification/mail-notification-3.0/src/mn-evolution-glue.gob:61: undefined reference to `mail_tool_uri_to_folder'
.libs/liborg_gnome_mail_notification_la-mn-evolution-glue.o: In function `mn_evolution_glue_getFolderName':/home/robb/build/mail-notification/mail-notification-3.0/src/mn-evolution-glue.gob:126: undefined reference to `mail_tool_uri_to_folder'
collect2: ld returned 1 exit status
make[4]: *** [liborg-gnome-mail-notification.la] Error 1
make[3]: *** [all] Error 2
make[2]: *** [all-recursive] Error 1
make[1]: *** [all] Error 2
make: *** [build-stamp] Error 2

```

---

### Post by hod139 on 2006-06-27
if ```
./configure; make 
```
works, you should be able to use checkinstall.  You can install checkinstall from the repos.  The process of making a deb then becomes
```
./configure; make
sudo checkinstall
```
suppling a decent version number and answering yes to the default questions is usually fine.

---

### Post by SpEcIeS on 2006-06-27
Thanks, but I am using ***dh_make -e [email]myemail@email.com[/email] -f ../file.tar.gz*** and ***dpkg-buildpackage*** method. I have been having some great success with other software, however this one fails. When building the deb for liferea 1.0.16 it too failed, but some alterations to *rules*  in the debian directory had to made then there was success. Most likely the same will apply here.

In the past when using checkinstall I have run into some scrollkeeper issues, so I choose not to use it.

For now I have Mail-Notification 3.0 installed manually and it is pretty nice :)

Thanks for you interest. ;)

---

### Post by hod139 on 2006-06-27
I haven't gone the dpkg-buildpackge route in a very long time.  The time I did I used this howto:
[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)
For all I know there is a better guide out there though.

---

### Post by SpEcIeS on 2006-06-27
After reading all of the Ubuntu Howto's I decided to stay away form chroot, it would just eat up HDD space. What I build I use anyway, so this would really put my packages to the test. It would be nice to have other test them too. :)

The debian tutorials are great and then apply the ubuntu alterations.

---

