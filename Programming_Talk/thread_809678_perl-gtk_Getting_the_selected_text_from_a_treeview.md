---
title: "perl-gtk: Getting the selected text from a treeview"
date: 2008-05-27
forum: Programming Talk
---

### Post by aullidolunar on 2008-05-27
Hi, guys!

I'm trying to get the selected text from a treeview, this is my treeview creation:
```

$ls = Gtk2::ListStore->new("Glib::String");
$tv1 = Gtk2::TreeView->new($ls);
my $rt = Gtk2::CellRendererText->new;
my $tvcol1 = Gtk2::TreeViewColumn->new_with_attributes("Playlist", $rt, "text", 0);
$tv1->append_column($tvcol1);
$panel->pack_start($tv1, TRUE, TRUE, 0);

```
I know how to add the texts on the listview:
```

$ls->set($ls->append, 0, "joel");

```
But, how do I get the selected item text?
This is how I'm attempting to do:
```

my $text = $tv1->get_selection->get_text;

```
Thanks for any tip :)

---

### Post by slavik on 2008-05-27
have you looked at the gtktreeview documentation? (the C one)

---

