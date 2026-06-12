---
title: "firefox is messing up alsa and screwing up a lot of other things"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-08-28
i decided since this happens everytime that id run it in the terminal and see what it says while i use it. when it errored i got this message.


ALSA lib pcm_dmix.c:874:-(snd_pcm_dmix_open) unable to open slave



(firefox:7722): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed



(firefox:7722): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed



(firefox:7722): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed



(firefox:7722): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

---

### Post by sdennie on 2008-08-28
By "messing up alsa" do you mean that you have no sound?  If so, this might be able to fix it: [ HOWTO: PulseAudio Fixes & System-Wide Equalizer Support (Hardy Heron)]("http://ubuntuforums.org/showthread.php?t=789578").  Alternatively, you could stop using PulseAudio by going to System->Preferences->Sound and switching everything to ALSA.

As for the other gtk errors, if there is no visual problem with the way FireFox works, it may be safe to ignore them.  If those errors are causing genuine problems then I would check to see if it's one of your plugins that is causing them.

---

