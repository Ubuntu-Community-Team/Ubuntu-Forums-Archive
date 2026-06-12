---
title: "pcmanfm command line option to open new window?"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by sideburn on 2012-01-13
Hey nix-users!

I'm stumped on this one... what is the option for opening a new window with pcmanfm command? I tried $man pcmanfm and $pcmanfm --help but no luck. The closest I found was opening a new tab with '-t' option. For example to open trash window as a new tab in existing window:
```
$pcmanfm -t trash:///
```

I can open new window with CTRL + N if my memory is correct. I'm away from my computer at this moment. I hope I can achieve this thru command line.

Thanks! :-)

---

### Post by Rainbow_Dash on 2012-01-13
Wouldn't it just be pcmanfm without any options??

I've never used it but some applications are setup to allow multiple instances, and some aren't.

---

### Post by sideburn on 2012-01-13
Without any options pcmanfm opens new tab by default.

Is there such a command where you can invoke CTRL + N?

---

### Post by ogilvierothchild on 2012-02-15
> **sideburn said:**
> Hey nix-users!

I'm stumped on this one... what is the option for opening a new window with pcmanfm command? I tried $man pcmanfm and $pcmanfm --help but no luck. The closest I found was opening a new tab with '-t' option. For example to open trash window as a new tab in existing window:
```
$pcmanfm -t trash:///
```

I can open new window with CTRL + N if my memory is correct. I'm away from my computer at this moment. I hope I can achieve this thru command line.

Thanks! :-)

I didn't find any solution other than doing 

```

sudo aptitude install apt-src build-essential
sudo aptitude build-dep pcmanfm
mkdir ~/src
cd ~/src
apt-src install -b pcmanfm

gedit pcmanfm-0.9.10/src/pcmanfm.c

```

Now I use emacs for my editor, but the point is, change line 421 in pcmanfm-0.9.10/src/pcmanfm.c from 
```

gboolean pcmanfm_open_folder(GAppLaunchContext* ctx, GList* folder_infos, gpointer user_data, GError** err)
{
    GList* l = folder_infos;
    for(; l; l=l->next)
    {
        FmFileInfo* fi = (FmFileInfo*)l->data;
        fm_main_win_open_in_last_active(fi->path); 
    }
    return TRUE;
}

```

to 
```

gboolean pcmanfm_open_folder(GAppLaunchContext* ctx, GList* folder_infos, gpointer user_data, GError** err)
{
    GList* l = folder_infos;
    for(; l; l=l->next)
    {
        FmFileInfo* fi = (FmFileInfo*)l->data;
        //fm_main_win_open_in_last_active(fi->path); // new-win fix 
	fm_main_win_add_win(NULL, fi->path);         // new-win fix
    }
    return TRUE;
}

```

Save and exit your text editor.  Back at the shell, type:
```

cd pcmanfm-0.9.10
dpkg-buildpackage -rfakeroot -uc -b
cd ..
sudo dpkg -i pcmanfm*deb

```

Now you can kiil and restart pcmanfm, or just logout/login.

---

