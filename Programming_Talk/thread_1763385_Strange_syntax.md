---
title: "Strange syntax"
date: 2011-05-20
forum: Programming Talk
---

### Post by tbastian on 2011-05-20
I was reading some source code, and I came accross the following as a function argument:
```
_("random string")
```
The function wanted a ```
const gchar *
``` Does anybody know what the leading underscore and the brackets mean?

---

### Post by cgroza on 2011-05-20
> **tbastian said:**
> I was reading some source code, and I came accross the following as a function argument:
```
_("random string")
```The function wanted a ```
const gchar *
``` Does anybody know what the leading underscore and the brackets mean?
It is probably some macro. I do not work with glib so I can't tell you more.
I have a hunch that it has a role to help in the internationalization of the application (special characters present in other languages and all that).

---

### Post by simeon87 on 2011-05-20
> **cgroza said:**
> It is probably some macro. I do not work with glib so I can't tell you more.
I have a hunch that it has a role to help in the internationalization of the application (special characters present in other languages and all that).

That's correct, it's part of gettext's interface for getting all the strings that need to be translated, see e.g., [here](http://www.gnu.org/software/gettext/).

---

### Post by cgroza on 2011-05-20
> **simeon87 said:**
> That's correct, it's part of gettext's interface for getting all the strings that need to be translated, see e.g., [here]("http://www.gnu.org/software/gettext/").
Ohh, I already use it, it is just the OP did not provide more context.
Also, does that come with glib standard headers, or you must include the gettext headers by yourself?

---

### Post by simeon87 on 2011-05-20
> **cgroza said:**
> Ohh, I already use it, it is just the OP did not provide more context.
Also, does that come with glib standard headers, or you must include the gettext headers by yourself?

Well, there's not much context in the OP but a string and _ in existing source is often gettext. I don't know if it's part of glib. In any case, instructions for integrating it are [here](http://www.gnu.org/software/gettext/FAQ.html#integrating_howto).

---

### Post by wojox on 2011-05-20
It means it's private. ;)

---

### Post by cgroza on 2011-05-20
> **simeon87 said:**
> Well, there's not much context in the OP but a string and _ in existing source is often gettext. I don't know if it's part of glib. In any case, instructions for integrating it are [here]("http://www.gnu.org/software/gettext/FAQ.html#integrating_howto").
wxWidgets has a _() macro which is used on literals, and it returns a wxString.

---

### Post by tbastian on 2011-05-20
Thanks a lot guys! It really confused me. Here's the context:
```
filechooserdialog1 = gtk_file_chooser_dialog_new (_("Please choose"), NULL, GTK_FILE_CHOOSER_ACTION_OPEN, NULL, NULL);
```

---

### Post by Petrolea on 2011-05-20
> **tbastian said:**
> Thanks a lot guys! It really confused me. Here's the context:
```
filechooserdialog1 = gtk_file_chooser_dialog_new (_("Please choose"), NULL, GTK_FILE_CHOOSER_ACTION_OPEN, NULL, NULL);
```

Try with and without. If you look carefully you will notice a difference ;)

---

