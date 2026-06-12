---
title: "Display terminal output??"
date: 2005-09-26
forum: Programming Talk
---

### Post by Ride Jib on 2005-09-26
Ok, I am finally getting around to creating my first linux application. I'm working with Glade and C++. 

Now, before I get into the heart of my program, I want to have a panel (terminal) showing me everything that is going on in the backgroud (for debugging purposes). For example, I want to automatically install a .bin file, but I want to be able to see that I am not receiving error messages from this process. Any ideas on how to do this, or links with information that might be helpful?

Thanks

---

### Post by banadushi on 2005-09-27
Why not just print out debugging info to the console if the program is started with a '-v' flag?.  Just use getopt to see if you got a '-v' flag, and then everywhere you need to write output, just wrap it in an 'if' statement.  Check out the GETOPT(3) man page for a quick and dirty example.

Have a good one.

Jason

---

### Post by thumper on 2005-09-27
[QUOTE=banadushi]Why not just print out debugging info to the console if the program is started with a '-v' flag?.  Just use getopt to see if you got a '-v' flag, and then everywhere you need to write output, just wrap it in an 'if' statement.  Check out the GETOPT(3) man page for a quick and dirty example.

Have a good one.

Jason[/QUOTE]
I can really recommend [boost program options]("http://www.boost.org/doc/html/program_options.html") instead of getopt.  The examples are reasonably easy to follow and make for a better command line parser.

That said, I do agree with the writing to standard output when in verbose mode (-v or --verbose).

---

### Post by Ride Jib on 2005-09-27
Alright, thanks for the input. I will give it a whirl...

---

### Post by LordHunter317 on 2005-09-27
[QUOTE=Ride Jib]Alright, thanks for the input. I will give it a whirl...[/QUOTE]
If it's error output or would interfer with the normal output of the program, place it on cerr and not cout.

---

### Post by Ride Jib on 2005-09-27
What I actually had in mind was something along the lines of Synaptics "Terminal" view. Anyone know how this was done?

---

### Post by wmcbrine on 2005-09-27
I don't know how it's done in Synaptic, but if you only need the output, I suggest popen(). I just hacked up a quick and dirty version of this with Glade -- made a window, dropped a Text View in it, and edited main() as follows:

```

int
main (int argc, char *argv[])
{
  GtkWidget *window1, *textview1;
  GtkTextBuffer *text;
  FILE *commandoutput;
  int currchar;
  gchar addit[2];

#ifdef ENABLE_NLS
  bindtextdomain (GETTEXT_PACKAGE, PACKAGE_LOCALE_DIR);
  bind_textdomain_codeset (GETTEXT_PACKAGE, "UTF-8");
  textdomain (GETTEXT_PACKAGE);
#endif

  gtk_set_locale ();
  gtk_init (&argc, &argv);

  add_pixmap_directory (PACKAGE_DATA_DIR "/" PACKAGE "/pixmaps");

  /*
   * The following code was added by Glade to create one of each component
   * (except popup menus), just so that you see something after building
   * the project. Delete any components that you don't want shown initially.
   */
  window1 = create_window1 ();
  gtk_widget_show (window1);

  textview1 = lookup_widget(window1, "textview1");
  text = gtk_text_view_get_buffer((GtkTextView *) textview1);

  commandoutput = popen("ls -al", "r");

  addit[1] = '\0';

  while ((currchar = fgetc(commandoutput)) != EOF) {
    addit[0] = currchar;
    gtk_text_buffer_insert_at_cursor(text, addit, 1);
  }

  pclose(commandoutput);

  gtk_main ();
  return 0;
}

```

---

### Post by LordHunter317 on 2005-09-28
[QUOTE=Ride Jib]What I actually had in mind was something along the lines of Synaptics "Terminal" view. Anyone know how this was done?[/QUOTE]
You don't want to do this unless your application is a daemon or some other sort of service.  Debug output to the terminal, normally with the ability to disable is the norm and standard, even for X11 applications.

---

