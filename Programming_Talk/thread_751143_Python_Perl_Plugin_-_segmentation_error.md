---
title: "Python Perl Plugin - segmentation error"
date: 2008-04-10
forum: Programming Talk
---

### Post by dchurch24 on 2008-04-10
Hi all,

This is my first attempt at a Pidgin plugin:

```


use Purple;

%PLUGIN_INFO = (
    perl_api_version => 2,
    name => "MythTV OSD Display",
    version => "0.1",
    summary => "Displays the content of messages in Myth",
    description => "Displays the content of messages received whilst not at the IM machine",
    author => "Dave Smith <dave\@consumeractiongroup.co.uk>",
    url => "http://www.cidb.co.uk",

    load => "plugin_load",
    unload => "plugin_unload"
    );

    sub plugin_init {
      return %PLUGIN_INFO;
    }

    sub plugin_unload {
      my $plugin = shift;
      Purple::Debug::info("testplugin", "plugin_unload() - Test Plugin Unloaded.\n");
    }

    sub plugin_load {
     my $plugin = shift;
     Purple::Signal::connect(Purple::Conversations::get_handle(), "received-im-msg", $plugin, \&signal_msgin, "");
    }

    sub signal_msgin { #(account, sender, message, conv, flags)
      system("mythtvosd mythtvosd --template=scroller --scroll_text=\"Message from MSN!\"", "Pidgin" );
      Purple::Debug::info("speak_message()", "MythTV OSD Plugin Spoke.");
    }


```

...which nearly works!

The problem is that when the user has an incoming message the plugin_load() runs, then creates a segmentation fault and pidgin just crashes.

No more debug info - just crashes.

I have even taken out all the code in signal_msgin, and the crash still occurres.

Any ideas?

---

### Post by dchurch24 on 2008-04-10
I thought it might be worth mentioning that this is the 64 bit version of Pidgin.

---

### Post by Hichhiker on 2009-04-23
Sorry to dig up old thread but did you ever track this down? I am beating my head against exact same issue (also 64bit intrepid).

Thanks.

-HH

---

### Post by dchurch24 on 2009-04-29
I'm afraid not :-(

In the end I ran it on my daughter's machine (Xubuntu 32 bit) and it worked fine - it just means I have to be logged in on her machine rather than mine, which is a bit of a pain.

---

