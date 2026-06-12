---
title: "Can you make a virtual directory path"
date: 2019-08-08
forum: New to Ubuntu
---

### Post by graphicsguy on 2019-08-08
I'm very new to ubuntu and have just set up my webserver. What I am wondering is if there is a way to create virtual directory paths.
I have a real directory at *[www.[mydomain].com/rin/tmpl/images](www.[mydomain].com/rin/tmpl/images)*
I would like to be able to have *[www.[mydomain].com/myimages](www.[mydomain].com/myimages)* act as an alias to the real directory that I listed first.

So that
*[www.[mydomain].com/rin/tmpl/images](www.[mydomain].com/rin/tmpl/images)* would show the same contents as *[www.[mydomain].com/myimages](www.[mydomain].com/myimages)*
and
*[www.[mydomain].com/rin/tmpl/images/cab.jpg](www.[mydomain].com/rin/tmpl/images/cab.jpg)* would show the same file as [I][www.[mydomain].com/myimages/cab.jpg](www.[mydomain].com/myimages/cab.jpg)

Is this something that is possible?
[/I]

---

### Post by SeijiSensei on 2019-08-08
If you're using Apache, the simplest method is with an [Alias]("https://httpd.apache.org/docs/2.4/mod/mod_alias.html#alias") statement in the definition for the VirtualHost.

```

<VirtualHost *:80>
ServerName
[etc.]
Alias /myimages /path/to/www.[mydomain].com/rin/tmpl/images
[etc.]

```

You'll need to enter the complete path to the aliased directory.

The other option is to use [symbolic links]("https://askubuntu.com/questions/56339/how-to-create-a-soft-or-symbolic-link"), commonly called "symlinks." These operate at the operating system level.  By default, symlinks are disabled in Apache, but you can add the directive "Options FollowSymlinks" in the <Directory> stanza for any directories you want them enabled.

---

