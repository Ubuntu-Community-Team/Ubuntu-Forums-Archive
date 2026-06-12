---
title: "Run a .desktop from a python script"
date: 2010-12-02
forum: Programming Talk
---

### Post by Konomics on 2010-12-02
Hi all,

I'm trying to write a python script that includes the ability to list all programmes in the gnome menu and allow the user to run them. By using the source code of other programs, I've managed to work out how to list all the programs (unfortunately I haven't been able to find any good documentation for the api). However I haven't yet managed to work out how to execute programs on this list. 

I've put the relevant bits of code together to make a little program that finds the first launcher on the menu and runs it:

```

import gmenu

def run(launcher):
  # TODO: run program here
  pass

def run_first_launcher(parent):
  for item in parent.get_contents():
    if item.get_type() == gmenu.TYPE_DIRECTORY:
      run_first_launcher(item)
    else:
      print "Executing " + item.name + "..."
      run(item)
    break

tree = gmenu.lookup_tree("applications.menu")
run_first_launcher(tree.root)

```

---

### Post by ssam on 2010-12-02
might be a better way, but this seems to work

```
os.system("xdg-open /usr/share/applications/gedit.desktop")
```

---

