---
title: "html2pop3: JAVA jre 1.5.0 64bit run-time problem"
date: 2007-06-08
forum: Programming Talk
---

### Post by macubo on 2007-06-08
Hi all, I need to get mails from providers who forbits to do it if the adsl you're using is not theirs.. so I use [html2pop3]("http://www.baccan.it/index.php?sezione=html2pop3&email=si") which is a simple bridge html-pop3 allowing you to read your email directly from your client..

It is done in java 4, but, as I'm running Ubuntu Feisty 64bit, I took from the repos the sun-java5-jdk (and jre), version 5.0u11, and plan to use it with Eclipse.

When I run the start-up script (./html2pop3 start), I get the following:
```
manuele@manuele-laptop:/usr/local/bin/html2pop3-2.32$ ./html2pop3.sh start
Avvio di html2pop3...
manuele@manuele-laptop:/usr/local/bin/html2pop3-2.32$ Exception in thread "Thread-2" Exception in thread "Thread-4" Exception in thread "Thread-3" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at org.html2pop3.utils.MsgBox.<init>(MsgBox.java:19)
   at smtpServer.run(smtpServer.java:77)
Caused by: java.lang.NoClassDefFoundError: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...5 more
java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at org.html2pop3.utils.MsgBox.<init>(MsgBox.java:19)
   at nntpServer.run(nntpServer.java:77)
Caused by: java.lang.NoClassDefFoundError: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...5 more
java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at org.html2pop3.utils.MsgBox.<init>(MsgBox.java:19)
   at pop3Server.run(pop3Server.java:116)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: impossibile aprire il file oggetto condiviso: Nessun file o directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...5 more

manuele@manuele-laptop:/usr/local/bin/html2pop3-2.32$ ./html2pop3.sh stop
Chiusura di html2pop3

```

This is the script:
```
manuele@manuele-laptop:/usr/local/bin/html2pop3-2.32$ cat html2pop3.sh
#! /bin/bash
# Autore Originale: vito <malco@tim.it>
# Avvia, riavvia, ferma e controlla html2pop3
# Successive modifiche: flevour <html2pop3@flevour.net>
# Changelog: 
# 18/06/04 - il processo html2pop3 viene ora terminato con un kill del pid e non con un killall di ogni java


# Modificare con il percorso assoluto dell'interprete java
JAVA=/usr/bin/java

# Modificare con il percorso assoluto di html2pop3
HTML2POP3=/usr/local/bin/html2pop3-2.32/

# paramentri passati all'interprete java
COMANDO=" -cp html2pop3.jar:httpclient.jar:httpmail.jar:xercesImpl.jar:xmlParserAPIs.jar html2pop3"


case "$1" in
    start)
        check=`pgrep -f -- "$COMANDO"`
        if [ "$check" = "" ]; then
                cd $HTML2POP3
                echo -n "Avvio di html2pop3..."
                echo
                # html2pop3 in background...
                $JAVA $COMANDO&
        else
                echo -n "html2pop3 e' gia' in esecuzione"
                echo
        fi
        ;;
    stop)
        echo -n "Chiusura di html2pop3"
        echo
        ## Termina html2pop3 con killall attendendo l'avvenuta chiusura
        pid=`pgrep -f -- "$COMANDO"`
        kill -9 $pid
        ;;    
    status)
        echo -n "Controllo lo stato di html2pop3: "
        echo
        ## Controlla lo stato html2pop3
        ps -p 1 `pgrep -f -- "$COMANDO"` |
                 awk '{ORS="" ; if ($3 ~ /^[TWXZ]/) {print "1"} else print "0"}' |
                  awk '{if ($1 > 0) {print "Il processo ha qualche problema oppure e` inattivo"} else {print "Il processo e` attivo"} }'
        ;;
    restart)
        echo -n "Chiusura di html2pop3"
        echo
        ## Termina html2pop3 con killall attendendo l'avvenuta chiusura
        pid=`pgrep -f -- "$COMANDO"`
        kill -9 $pid

        cd $HTML2POP3
        echo -n "Riavvio di html2pop3.."
        echo
        # html2pop3 in background....
        $JAVA $COMANDO&
        ;;    
    *)
        echo "Sintassi: $0 {start|stop|status|restart}"
        exit 1
        ;;
esac

```

It seems a problem related to java language, maybe some incompatibility between java 4 and 5, but on winXP I currently use JRE 5.0u11 with no problems. May this be a 64bit issue?

Any help appreciated. Thank you


[I]EDIT: Got it working... sorry but it seems that I can only find the solution AFTER posting for some help from you..
Anyway, found [this]("https://bugs.launchpad.net/ubuntu/+source/gcj-4.1/+bug/90380"). Some minor problems however persist, infact I cannot see the GUI interface, while the server works perfecly.[/I]

---

### Post by txcrackers on 2007-06-10
It looks like you still have GCJ installed, which takes "precedence" over the Java 5 JVM. Uninstall GCJ (if you can), otherwise you'll have to mess around with *update-alternatives* to ensure the Java 5 JVM is your default "java"

---

### Post by ryan76 on 2007-06-16
Awesome, this worked for me, thanks.

---

