---
title: "Applying a patch"
date: 2018-10-17
forum: New to Ubuntu
---

### Post by hkg563 on 2018-10-17
Hello, I am very new to Ubuntu, I'm still learning the ropes, and one of the things I want to do is making Gnome run at 144fps. I already set resolution and refresh rate to 144, but Gnome seems to still be running at 60fps.
After some research I came upon a couple of patches that seemingly fix this; however, I have no idea how to apply them, since they're just code that comes inside a text file. 

```
--- a/clutter/clutter/cogl/clutter-stage-cogl.c
+++ b/clutter/clutter/cogl/clutter-stage-cogl.c
@@ -179,11 +179,11 @@
 
   refresh_rate = stage_cogl->refresh_rate;
   if (refresh_rate == 0.0)
-    refresh_rate = 60.0;
+    refresh_rate = 144.0;
 
   refresh_interval = (gint64) (0.5 + 1000000 / refresh_rate);
   if (refresh_interval == 0)
-    refresh_interval = 16667; /* 1/60th second */
+    refresh_interval = 6945;
 
   stage_cogl->update_time = stage_cogl->last_presentation_time + 1000 * sync_delay;
 
--- a/clutter/clutter/clutter-pan-action.c
+++ b/clutter/clutter/clutter-pan-action.c
@@ -69,7 +69,7 @@
 #define FLOAT_EPSILON   (1e-15)
 
 static const gfloat min_velocity = 0.1f; // measured in px/ms
-static const gfloat reference_fps = 60.0f; // the fps assumed for the deceleration rate
+static const gfloat reference_fps = 144.0f; // the fps assumed for the deceleration rate
 static const gfloat default_deceleration_rate = 0.95f;
 static const gfloat default_acceleration_factor = 1.0f;z
 
--- a/clutter/clutter/clutter-main.c
+++ b/clutter/clutter/clutter-main.c
@@ -99,7 +99,7 @@
 static gboolean clutter_enable_accessibility = TRUE;
 static gboolean clutter_sync_to_vblank       = TRUE;
 
-static guint clutter_default_fps             = 60;
+static guint clutter_default_fps             = 144;
 
 static ClutterTextDirection clutter_text_direction = CLUTTER_TEXT_DIRECTION_LTR;
 
--- a/src/compositor/meta-window-actor.c
+++ b/src/compositor/meta-window-actor.c
@@ -969,7 +969,7 @@
     }
   else
     {
-      refresh_rate = 60.0f;
+      refresh_rate = 144.0f;
     }
 
   current_time =
```

How do I make this code run?
I'm a complete noob, I really appreciate any help you can give me!

---

### Post by TheFu on 2018-10-17
C doesn't run directly.  It has to be compiled, then linked.  That happens after you apply the patch to the source code, so you'll need to get that and follow build instructions for all the dependencies and the related gnome code.

Doing this is well beyond most Linux users.  This is less about Linux and more about being a C programmer with skills to build a complex project like Gnome.

I was a professional C programmer for about 15 yrs. Assuming everything goes perfectly, I'd expect something like this to take 4-8 hrs of time, best case.  Much of that time would be learning about gnome's build methods and getting all the required dependencies compiled first.  Basically, setting up a C development environment just to change those 3 lines.  I wouldn't be surprised if other areas of the code needed some changes too.  I've never touched Gnome code before.  For  someone on the team, they could do it faster for the version they are currently working on, but doing it for the exact version you are using today will take them some time too.  Plus, you'd need to redo everything anytime that specific gnome library was updated. I have no idea how often that happens, weekly? Monthly? quarterly?

A more efficient answer would be to make changing between different refresh rates a configuration option and then for end-users to wait for that update to make it into any distros in months to a year time.  Since it is a new capability, backporting isn't something that would likely happen.  This assumes that the Gnome project team accepts the code changes. They might not.

Hope this explanation is helpful.

---

### Post by monkeybrain20122 on 2018-10-17
As said to apply a patch you need to compile mutter from source which is not a simple job esp if you are a beginner. There may be a much easier workaround

                        ```


sudo -H gedit /etc/environment

```

add the line 
     ```
CLUTTER_DEFAULT_FPS=144
```
   or whatever your monitor's real refresh rate is.

Save
 
Reboot.

See last post from [https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1763892](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1763892)

---

### Post by hkg563 on 2018-10-17
Ah, I see, so this is well beyond my abilities. I guess it's just as useful to learn about my limitations (especially as a noob).
Thank you for your response!

---

### Post by hkg563 on 2018-10-18
> As said to apply a patch you need to compile mutter from source which is  not a simple job esp if you are a beginner. There may be a much easier  workaround


Oh, I hadn't seen this post, silly me. When I try to edit the environment file in /etc I find out it's Read-Only and can only save as. Is there a way to grant the ability to modify this file?

---

### Post by deadflowr on 2018-10-18
> **hkg563 said:**
> Oh, I hadn't seen this post, silly me. When I try to edit the environment file in /etc I find out it's Read-Only and can only save as. Is there a way to grant the ability to modify this file?

Run the first command monkeybrain20122 posted.

---

### Post by TheFu on 2018-10-18
> **hkg563 said:**
> Ah, I see, so this is well beyond my abilities. I guess it's just as useful to learn about my limitations (especially as a noob).
Thank you for your response!

We all have limitations.  Assuming the suggested workaround actually works - BTW, it is much better solution than modifying code - then you have a solution.   monkeybrain20122 knows this stuff better than me, I strongly suspect.

I wouldn't use the command provided, but it should work AND it is safe.

I would use ```
sudoedit  /etc/environment
```.  sudoedit is designed to always be safe to use when you need to modify almost all system files.  Unix systems, including Linux, are secured using file and directory permissions. This is a basic skill to understand and master. Unix systems are multi-user from the ground up, even if you are the only human using the machine.  These permissions are important for a number of reasons and learning them sooner than later will make most permissions issues easy to solve without negatively impacting the entire security of the system.  Google "Linux file permissions tutor" to get step-by-step tutorial and introduction.  There are many of them online.  Generally, all of them will teach 98% of what you'll use commonly related to Unix permissions.  

All Unix-based operating systems follow the same model, so everything you learn will apply to pretty much every OS you will use, except 1 (MS-Windows). OSX, iOS, Android, and all commercial versions of Unix follow the same POSIX permissions.  All of them.  It is useful knowledge.

---

### Post by hkg563 on 2018-10-19
Thank you very much for your help, guys, I used monkeybrain20122's command and now the interface looks smooth as silk. Only Firefox is still running at 60fps but I can live with that.

TheFu, I'll read up on permissions, I really want to learn how to use Linux properly.

Again, many thanks to all who posted in this thread for helping me out!

---

