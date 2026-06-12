---
title: "Using libunity in C/C++"
date: 2011-05-14
forum: Programming Talk
---

### Post by sajimon on 2011-05-14
Hello,

I'm trying to familiarize myself with new unity API provided by libunity, I wrote a simple example application, but it is doesn't seems to work. 

Heres the testing code, if someone could take a look

```
#include <unity/unity/unity.h>

int main(int argc, char **argv)
{

    g_type_init();
    UnityLauncherEntry* xx = unity_launcher_entry_get_for_desktop_id("evolution.desktop");
    unity_launcher_entry_set_count(xx,12);
    unity_launcher_entry_set_count_visible(xx,TRUE);

    pause();
return 0;
}

```There is no effect at all, std output not showing any messages or warnings as well

---

### Post by cgroza on 2011-05-14
> **sajimon said:**
> Hello,

I'm trying to familiarize myself with new unity API provided by libunity, I wrote a simple example application, but it is doesn't seems to work. 

Heres the testing code, if someone could take a look

```
#include <unity/unity/unity.h>

int main(int argc, char **argv)
{

    g_type_init();
    UnityLauncherEntry* xx = unity_launcher_entry_get_for_desktop_id("evolution.desktop");
    unity_launcher_entry_set_count(xx,12);
    unity_launcher_entry_set_count_visible(xx,TRUE);

    pause();
return 0;
}

```There is no effect at all, std output not showing any messages or warnings as well

Don't you think there should be some kind of main loop? I am guessing the program executes, and when it's done, the entry goes away too.

---

### Post by sajimon on 2011-05-15
Ok, I changed pause() function, to gtk_main(); and it worked.
Obviously something else important happening in gtk_main() for this api to work.

thanks for clue.

---

### Post by t1497f35 on 2011-05-15
> #include <unity/unity/unity.h>
I suspect someone at Canonical is mad about tautology.

---

### Post by cgroza on 2011-05-15
> **t1497f35 said:**
> I suspect someone at Canonical is mad about tautology.
Kind of weird that directory hierarchy. Maybe because there are others libraries in the Unity folder.

---

### Post by mhr3 on 2012-06-25
The correct usage is:

```

#include <unity.h>

int main(int argc, char **argv)
{
    g_type_init();

    UnityLauncherEntry* entry =
        unity_launcher_entry_get_for_desktop_id ("evolution.desktop");
    unity_launcher_entry_set_count (entry, 12);
    unity_launcher_entry_set_count_visible (entry, TRUE);

    GMainLoop *ml = g_main_loop_new (NULL, FALSE);
    g_main_loop_run (ml);

    return 0;
}

```

Considering the file is called test.c, you can compile it with ```

gcc -o test test.c `pkg-config --cflags --libs unity`

```

---

