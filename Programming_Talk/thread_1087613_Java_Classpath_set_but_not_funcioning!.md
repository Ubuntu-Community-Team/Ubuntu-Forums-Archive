---
title: "Java Classpath set but not funcioning!"
date: 2009-03-05
forum: Programming Talk
---

### Post by theDaveTheRave on 2009-03-05
Hi all.

So I recently upgraded my Hardy system to Intrepid, and i decided that this time I WAS GOING TO GET THE CLASSPATH THING RIGHT.

I'm using the Mysql:jdbc connector,

When I was using hardy I couldn't get the classpath to work, so I ended up degenerating to putting the jar file into the JRE...

```

/usr/lib/jvm/java-[version]/jre/lib/ext$

```

But now I'm getting a little more serious and I've decided I should really do this correctly as I've read that putting the file here is "bad form" and can lead to "strange" problems!

so I did some hunting, eventually I found that I could edit the <etc/environment> file and add the classpath details there. So I did, here is the output of this filedavem

```

@Dartagnon:~$ more /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
CLASSPATH="$CLASSPATH:/home/davem/Java/ConnectorJ/mysql-connector-java-5.1.7/mysql-connector-java-5.1.7.bin.jar
davem@Dartagnon:~$

```

And still I get the same error of the class not being found when I attempt to run the file, here is the error message....

```

error in connecting.. again! java.lang.ClassNotFoundException: com.mysql.jdbc.Driver

```

I can confirm that the enviroment variable is correctly set...

```

davem@Dartagnon:~$ export
declare -x CLASSPATH="\$CLASSPATH:/home/davem/Java/ConnectorJ/mysql-connector-java-5.1.7/mysql-connector-java-5.1.7.bin.jar"
declare -x COLORTERM="gnome-terminal"
declare -x DBUS_SESSION_BUS_ADDRESS="unix:abstract=/tmp/dbus-0DnmrWQLN3,guid=e3a975ed05c06a30365c310b49afa820"
declare -x DESKTOP_SESSION="gnome"
declare -x DISPLAY=":0.0"
declare -x GDMSESSION="gnome"
declare -x GDM_LANG="en_GB.UTF-8"
declare -x GDM_XSERVER_LOCATION="local"
declare -x GNOME_DESKTOP_SESSION_ID="this-is-deprecated"
declare -x GNOME_KEYRING_PID="5835"
declare -x GNOME_KEYRING_SOCKET="/tmp/keyring-O2bNlV/socket"
declare -x GPG_AGENT_INFO="/tmp/seahorse-UzIirJ/S.gpg-agent:5927:1"
declare -x GTK_MODULES="gail:atk-bridge"
declare -x GTK_RC_FILES="/etc/gtk/gtkrc:/home/davem/.gtkrc-1.2-gnome2"
declare -x HISTCONTROL="ignoreboth"
declare -x HOME="/home/davem"
declare -x LANG="en_GB.UTF-8"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="davem"
declare -x LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:"
declare -x OLDPWD
declare -x ORBIT_SOCKETDIR="/tmp/orbit-davem"
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/real/RealPlayer"
declare -x PWD="/home/davem"
declare -x SESSION_MANAGER="local/Dartagnon:/tmp/.ICE-unix/5846"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_AUTH_SOCK="/tmp/keyring-O2bNlV/ssh"
declare -x TERM="xterm"
declare -x USER="davem"
declare -x USERNAME="davem"
declare -x WINDOWID="96469049"
declare -x WINDOWPATH="7"
declare -x XAUTHORITY="/home/davem/.Xauthority"
declare -x XDG_DATA_DIRS="/usr/local/share/:/usr/share/:/usr/share/gdm/"
declare -x XDG_SESSION_COOKIE="d85ce80a5f2f395c64568f764992ecb3-1236248606.895986-649492416"
davem@Dartagnon:~

```

Which would seem to be a good sign!

But why do I still get this error?? I just don't get it, the web site says that I should have this as my classpath target, so surelt it should work?

I have got a sort of solution, if I open the project in netbeans I can add properties to the project, if I then add the mysql-connectorJ....jar the package will work fine, alternatively I can add it too the options in netbeans.

However this doesn't seem "efficient" and  when I distribute my project these links are obviously going to fail horribly!

so some information / advice is required so as I can understand why my classpath setting isn't working (when it seems as though it should be) and if it is wrong, how to set it correctly, or a better solution for my projects when I come to distribute them.

Please note that ultimately I will most likely use some sort of application server, so maybe when that happens this problem will dissappear. However I intend to distribute the system as a stand alone  
application also.

thanks in advance for your time and comments.

David

---

### Post by jespdj on 2009-03-05
> **theDaveTheRave said:**
> I can confirm that the enviroment variable is correctly set...
```

davem@Dartagnon:~$ export
declare -x CLASSPATH="\$CLASSPATH:/home/davem/Java/ConnectorJ/mysql-connector-java-5.1.7/mysql-connector-java-5.1.7.bin.jar"
```
Except that there's this strange thing \$CLASSPATH as the first thing in your classpath. Try removing that. Also, try adding the current directory "." to the classpath:
```
CLASSPATH=".:/home/davem/Java/ConnectorJ/mysql-connector-java-5.1.7/mysql-connector-java-5.1.7.bin.jar"
```
You can also specify the classpath on the command line when you run your program, instead of using the CLASSPATH environment variable:
```
java -cp .:/home/davem/Java/ConnectorJ/mysql-connector-java-5.1.7/mysql-connector-java-5.1.7.bin.jar com.mypackage.MyProgram
```
Note that if you've packaged your program in a JAR file, and when you're using the "-jar" option to start your program, the JVM will NOT look at the CLASSPATH variable or the "-cp" switch. In that case, you must specify the classpath in the MANIFEST file inside your JAR file (see [Sun's tutorial about JAR files](http://java.sun.com/docs/books/tutorial/deployment/jar/) for details).

---

### Post by theDaveTheRave on 2009-03-05
> 
Except that there's this strange thing \$CLASSPATH as the first thing in your classpath.


Jespdj

I admit I thought that strange too, it is there as I have included the comment of $CLASSPATH in the </etc/environment> control field, so as I don't accidentally overide any other setting that are made from within the system? is there another way of doing this, or should I simply remove it, and will it cause me problems later on?

also the adding of the current directory is something I forgot.

I'll make the changes to the /etc/environmen file and test to see if it makes the whole thing work.

Thanks for the advice / assistance.

David.

---

