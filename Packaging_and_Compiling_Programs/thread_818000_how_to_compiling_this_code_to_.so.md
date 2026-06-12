---
title: "how to compiling this code to *.so ?"
date: 2008-06-04
forum: Packaging and Compiling Programs
---

### Post by biowee on 2008-06-04
there are source lines of "scim.c" as:

```

/*
 * Copyright (C) 2007-2008 Gauvain Pocentek <gpocentek@linutop.com>
 * 
 * Mostly taken from the gsynaptics mcs plugin
 * Copyright (c) 2004 Danny Milosavljevic <danny_milo@yahoo.com>
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; You may only use version 2 of the License,
 * you have no option to use any other version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA
 */

#ifdef HAVE_CONFIG_H
#include <config.h>
#endif

#ifdef HAVE_STDLIB_H
#include <stdlib.h>
#endif

#define EXE "scim-setup"
#define ICON "scim-setup"

/* static prototypes */
static void run_dialog (McsPlugin *);

/*
 */
McsPluginInitResult
mcs_plugin_init (McsPlugin * plugin)
{
	gchar *where = NULL;

	xfce_textdomain (GETTEXT_PACKAGE, LOCALEDIR, "UTF-8");

	plugin->plugin_name = g_strdup ("scim");
	plugin->caption = g_strdup (Q_("Button Label|Scim Input"));
	plugin->run_dialog = run_dialog;
	plugin->icon = xfce_themed_icon_load (ICON, 32);
	if (plugin->icon)
		g_object_set_data_full (G_OBJECT (plugin->icon),
		                        "mcs-plugin-icon-name",
					g_strdup (ICON),
					g_free);

	where = g_find_program_in_path (EXE);
	if (where)
	{
		g_free (where);
		return (MCS_PLUGIN_INIT_OK);
	}

	g_free (where);
	return (MCS_PLUGIN_INIT_ERROR);
}

/*
 *  */
static void
run_dialog (McsPlugin * plugin)
{
	xfce_exec(EXE, FALSE, FALSE, NULL);
}

```

I want to compliling it to the library file named "scim.so" as the command line as:
```

gcc scim.c -fPIC -shared -o scim.so

```

but it's error:

```

scim.c:39: error&#65306; expected ‘)’ before ‘*’ token
scim.c:44: error&#65306; expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mcs_plugin_init’
scim.c:74: error&#65306; expected ‘)’ before ‘*’ token

```

so, can I compiling it into scim.so?And how can I finish it?

thanks.

---

### Post by Vadi on 2008-06-04
There are errors in the code, from what it looks like there's a missing #include. But the guy's email is right there, try emailing the author.

---

### Post by jtrindle on 2008-06-04
Is there a configure program in the source directory?  Looks like you need to run it.

there should be a README of some kind in the same directory, with instructions on configuration.

It's possible you need some packages like xorg-dev installed to get the headers that define McsPlugin

---

### Post by biowee on 2008-06-05
now the question was solved. We can do as the command line:

gcc -DHAVE_CONFIG_H -I../.. -DLOCALEDIR=\"/usr/share/locale\" -shared -Wl,-soname -Wl,scim_plugin.so $(pkg-config --libs --cflags libxfce4mcs-manager-1.0 libxfcegui4-1.0) scim.c -o scim_plugin.so

---

