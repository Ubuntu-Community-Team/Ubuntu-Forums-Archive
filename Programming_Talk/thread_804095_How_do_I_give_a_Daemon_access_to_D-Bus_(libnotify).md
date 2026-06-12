---
title: "How do I give a Daemon access to D-Bus? (libnotify)"
date: 2008-05-22
forum: Programming Talk
---

### Post by MacGeneral on 2008-05-22
Hey everyone:

I wrote a small Application in C which uses libnotify and which should be executed in case that clamd finds a Virus (So I actually take a note that somethings wrong) - Its supposed to go in the VirusEvent line in clamd.conf.

The only problem is, that the user clamdaemon who runs clamd has no access to D-Bus which is why libnotify can't "tell" me that somethings wrong. (Don't know if it needs access to the Xserver somewhat as well).

Anyone has a good tutorial on how to configure D-Bus so it grants my application / the user clamdaemon access? The output shall appear on my Desktop (username macgeneral) of course!

Its my first application in C so don't be too hard ;)

It works if I run it on my user account.

```

#include <libnotify/notify.h>
#include <stdio.h>
#include <unistd.h>

int main(int argc, char * argv[]) 
{
	int i = 0;
	NotifyNotification *n;
	char buffer[255];

	strcpy(buffer, "A Virus was detected on your system!\n");

	if (argc == 2)
	{
		strcat(buffer, argv[1]);
	}
	else if (argc == 3)
	{
		strcat(buffer, argv[1]);
		strcat(buffer, " in file ");
		strcat(buffer, argv[2]);
	}
	else
	{
		for(i = 1; i < argc; i++ )
		{
			strcat(buffer, argv[i]);
			strcat(buffer, " ");
		}
	}

	notify_init("ClamAV Virus Event");

	n = notify_notification_new ("ClamAV", buffer, "/usr/share/pixmaps/Clam_icon.resized.png", NULL);

	notify_notification_set_urgency(n, NOTIFY_URGENCY_CRITICAL);

	notify_notification_set_timeout (n, 0); // no automatic timeout!

	if (!notify_notification_show (n, NULL)) 
	{
		fprintf(stderr, "Failed to send notification!\n");
		return 1;
	}

	g_object_unref(G_OBJECT(n));

	return 0;
}
```

---

