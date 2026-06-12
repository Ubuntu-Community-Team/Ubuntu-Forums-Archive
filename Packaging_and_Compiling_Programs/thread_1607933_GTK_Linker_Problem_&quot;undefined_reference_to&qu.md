---
title: "GTK Linker Problem &quot;undefined reference to&quot;"
date: 2010-10-28
forum: Packaging and Compiling Programs
---

### Post by mcemsi on 2010-10-28
Hallo zusammen,
ich versuche nun seit einiger Zeit ein gtk beispiel mit gcc in eclipse zu bauen aber es will einfach nicht funktionieren. :(

habe das libgtk2.0-dev package und die Abhängigkeiten installiert.

Ich compile das Ganze so:
gcc `pkg-config  --cflags --libs gtk+-2.0`

und habe den include path auf /usr/include/gtk-2.0/ gesetzt.

die Ausgabe auf der Konsole sieht folgendermaßen aus:
```

**** Build of configuration Debug for project Gtk ****

make all 
Building target: Gtk
Invoking: GCC C Linker
gcc  -o"Gtk"  ./main.o   
./main.o: In function `main':
/home/martin/workspace/Gtk/Debug/../main.c:15: undefined reference to `gtk_init'
/home/martin/workspace/Gtk/Debug/../main.c:17: undefined reference to `gtk_window_new'
/home/martin/workspace/Gtk/Debug/../main.c:18: undefined reference to `gtk_widget_show'
/home/martin/workspace/Gtk/Debug/../main.c:20: undefined reference to `gtk_main'
collect2: ld returned 1 exit status
make: *** [Gtk] Fehler 1

```

vielen Dank schonmal.
mcemsi

---

### Post by mcemsi on 2010-10-28
PS:
der Sourcecode ist das erste Beispiel von der offiziellen GTK Website.

---

### Post by mooobar on 2012-01-12
Vorab: Ich grabe gerne uralt-Threads aus, wenn sie exakt das gleiche Problem betreffen wie meins und ungelöst sind.

Ich habe ein "Game Of Life" in C mit GTK+-2.0 geschrieben, das unter dem Fedora in der Uni wunderbar baut, unter dem Xubuntu auf meinem Netbook (von 2009, kein dist-upgrade seitdem!) auch wunderbar baut, nur unter dem aktuellsten Ubuntu eben einfach nur für jede genutzte GTK-Funktion ein "undefined reference to `gtk_main'" (bzw. anderen Funktionsnamen am Ende) wirft - und logischerweise auch nichts baut am Ende.

Hat irgendjemand irgendwelche Vorschläge? Ich wäre sehr dankbar. (auch ein link zu einem anderen thread, der das behandelt, hilft - google seit 4 Stunden.)

---

### Post by mooobar on 2012-01-12
And the solution to my problem was:
"
 				 				   						 						 				 					 						[INDENT] 							You just have to swap the order of compile options. `pkg-config  --libs gtk+-2.0` has to be at the end. This is because the linker in  ubuntu automatically uses --as-needed or so."[/INDENT]

---

