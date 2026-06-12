---
title: "Gnome Mime Types - Please Help"
date: 2006-08-03
forum: Programming Talk
---

### Post by zootreeves on 2006-08-03
Hi, I am trying to set gnome so that it will open a specific file extension with my program and files with that extension will show the same icon as well.

So I figured out how to set the mime type for the file

```
<?xml version=\"1.0\" encoding=\"UTF-8\"?>
<mime-info xmlns=\"http://www.freedesktop.org/standards/shared-mime-info\">
    <mime-type type=\"application/x-cgwdtheme\">
        <comment>CGWD Theme</comment>
        <glob pattern=\"*.cgwdtheme.tar.gz\" />
  </mime-type>
</mime-info>
```
Save that as my_app.xml and put it in /usr/share/mime/packages

I have also figured out get the icon displayed by saving

```
application/x-myapp:
        description=My APP
        icon_filename=logo.png
        default_action_type=application
        short_list_application_ids_for_novice_user_level=myapp
        category=Audio/Visual

```

that as myapp.key and putting it in /usr/share/mime-info/

However I can't figure out how to do so that the user can double click the file and it will run a command (open in my program) - Does anyone know how to do this?

- Must all be done by the command line btw. Thanks

---

### Post by Van_Gogh on 2006-08-04
I'd be interested in this too. 

> **zootreeves said:**
> I have also figured out get the icon displayed by saving

```
application/x-myapp:
        description=My APP
        icon_filename=logo.png
        default_action_type=application
        short_list_application_ids_for_novice_user_level=myapp
        category=Audio/Visual

```

that as myapp.key and putting it in /usr/share/mime-info/

Does this mean that this way you can decide yourself the icon type for each mime type? I've been trying to have a Python icon for all my python(*.py) files, but haven't gotten it to work yet. Likewise, odt documents and pdf documents have the same icons at the moment(with nautilus set to no file preview, for performance reasons), which I think is annoying.

I'll definitely check this out later today.

---

### Post by Van_Gogh on 2006-08-05
I found [this tutorial]("http://www.fedoraforum.org/forum/archive/index.php/t-26875.html") which I think explains a lot. I think it solves your problem.

Me, I haven't yet found a way to set icons based on full mime-types rather than just partial mime type(i.e "text/x-python" rather than just "text") yet. I'll keep looking.

---

