---
title: "Glade and FileChooserDialogue"
date: 2009-01-22
forum: Programming Talk
---

### Post by mikeym on 2009-01-22
Hi,

I'm working on a Glade app at the moment (to add custom search buttons to firefox) and I'm struggling a bit with the file chooser dialogue. I can't seem to find anything which explains how to go about using it?

I've added a file chooser dialogue in Glade and put a couple of buttons on it (cancel and save) and it now looks like this: 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100711&stc=1&d=1232643953[/IMG]
 
Now I can run it like this from perl:

```

$filechooser->set_do_overwrite_confirmation (TRUE);
$filechooser->set_current_folder ($dir);
$filechooser->set_current_name ("$name.xml");
my $xmlfile;
if($filechooser->run=='accept-filename') {
	$xmlfile=$filechooser->get_filename;
}
$filechooser->destroy;

```

But it just displays dumbly and doesn't do anything. What do I have to do with my buttons to make it work?

Thanks again for all the help.

---

### Post by mikeym on 2009-01-22
I've found very little about this online, only a couple of mentions of the response ID of the buttons, but since this isn't working for me I can't confirm this. It appears that there may be a problem with Glade with regard to dialogues ([http://www.gtkforums.com/about1489.html](http://www.gtkforums.com/about1489.html)). 

I've however managed to work through a couple of C examples to get a FileChooserDialogue working with Perl. See [here]("http://mikeysfog.wikispaces.com/Perl+-+File+Chooser+Dialogue").

I'd still love to know if anyone's got any suggestions as to how to achieve the same with Glade 3.

---

### Post by jorgecs10 on 2009-01-23
maybe you don't need glade, look at [the documentation of the file chooser dialog]("http://library.gnome.org/devel/gtk/stable/GtkFileChooserDialog.html")

---

### Post by mikeym on 2009-01-23
Like I said, I've managed it through [pure code]("http://mikeysfog.wikispaces.com/Perl+-+File+Chooser+Dialogue") but it seems strange that Glade 3 doesn't seem to work for dialogues (especially when it has them by default!)

---

