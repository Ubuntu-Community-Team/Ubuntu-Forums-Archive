---
title: "Cannot compile Java in Emacs"
date: 2006-12-11
forum: Programming Talk
---

### Post by UltimateDevo on 2006-12-11
I'm running Ubuntu Edgy on a normal x86 machine, and I recently installed the Emacs21 package, the JDK package (1.5), and the JDE package. After writing a simple "Hello, World" program, I tried to compile from within Emacs using C-C C-V C-C. I get the error message: "Cannot find JDK's tools jar file (or equivalent). Type M-x describe-fucntion [RET] kde-get-jdk-dir for more info"

I imagine this means that Emacs can't find the compiler, but I'm not sure how to tell it. Tools.jar is contained in /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/lib/tools.jar

If the file has been compiled at the command line, it will run from emacs using C-C C-V C-R just fine.

Thanks

---

### Post by kaamos on 2006-12-11
You have to set all the JDE options by hand (compiler, jdk, etc..). See the JDE website for more info.

[http://jdee.sunsite.dk/jdedoc/html/jde-ug/jde-ug-content.html#RegisterSelectJDK](http://jdee.sunsite.dk/jdedoc/html/jde-ug/jde-ug-content.html#RegisterSelectJDK)

---

### Post by hod139 on 2006-12-11
Try this:
```

 sudo update-java-alternatives -s java-1.5.0-sun

```

---

### Post by UltimateDevo on 2006-12-11
Thanks for the help.

That seemed to do something, but it didn't let me compile. Now I get a different error:

> Specified BeanShell jar filed does not exist: /usr/share/emacs21/site-lisp/java/lib/bsh.jar

So I located bsh.jar in /usr/share/java and copied it in to the requested directory, which gives me a different error:

> // Error: EvalError: Class or variable not found: jde.util.CompileServer : at Line: 4 : in file: <unknown file> : jde .util .CompileServer .compile ( new String [ ] 
Compilation exited abnormally with code { at Mon Dec 11 14:24:49

---

### Post by mcglnx on 2006-12-11
Errr,... did you try an other IDE?
I'm using Eclipse everyday and it's very good in my opinion...

---

### Post by hod139 on 2006-12-11
I don't really know how to use emacs (I'm a vim kinda guy :evil:).  But for a sanity check can you compile your simple helloWorld app from the command line?

---

### Post by UltimateDevo on 2006-12-12
Yep, with no problems at all. In fact, if I compile from the command line, then I can run the compiled code from within emacs with no problems at all using C-C C-V C-R.

---

### Post by UltimateDevo on 2006-12-12
I tried punching the last error message into Google, and found the following on [http://kanis.eu/en/blog-2004-06.html](http://kanis.eu/en/blog-2004-06.html)
> 
I am getting the following (annoying) error message with JDE. It's a mode to edit Java in emacs.

bsh: Specified BeanShell jar filed does not exist:
/usr/share/emacs21/site-lisp/java/lib/bsh.jar

The following cures the problem:

cd /usr/share/emacs21/site-lisp
mkdir java
cd java
ln -s /usr/share/java lib

It looks like a bug in Debian, I might report it if I find the time

And what do you know, but it cured the problem. Thanks for all the help.

---

### Post by UltimateDevo on 2006-12-12
Although it seemed to get very confused on about half of the compiles while I had WINE installed with IE for Linux on it. It might compile, but it might also print out the contents of the .iexplorer directory, and the .wine directory and then quit. With those gone, no problems.

---

### Post by stairwayoflight on 2009-02-07
I'm having problems with this as well. I can compile now in JDEE, but I get an error in the minibuffer.

My Emacs version:
GNU Emacs 23.0.60.1 (x86_64-pc-linux-gnu, GTK+ Version 2.14.3) of 2008-10-13 on yellow, modified by Debian

(It is the current emacs-snapshot as provided by Intrepid.)

I have jde 2.3.5.1-5 from the intrepid repo.

When I compile, the message in the minibuffer is:
error in process filter: Wrong type argument: number-or-marker-p, "0"

My first compile took ~10 seconds. I'm not sure if that is an issue, but I have an Intel Q9550 quad core and javac compiles on the command line in under .8 seconds.

As far as trying update-alternatives, as my software's versions are different from the above, I tried:

[COLOR="black"][COLOR="black"][COLOR="Navy"]$ sudo update-java-alternatives -s java-6-sun-1.6.0.10[/COLOR][/COLOR][/COLOR]
update-java-alternatives: file does not exist: /usr/lib/jvm/.java-6-sun-1.6.0.10.jinfo
[COLOR="Navy"]$ ls -a /usr/lib/jvm[/COLOR]
.   java-6-openjdk         java-6-sun           .java-6-sun.jinfo
..  .java-6-openjdk.jinfo  java-6-sun-1.6.0.10
[COLOR="Navy"]$ sudo update-java-alternatives -s java-6-sun[/COLOR]
No alternatives for firefox-javaplugin.so.
No alternatives for iceape-javaplugin.so.
No alternatives for iceweasel-javaplugin.so.
No alternatives for midbrowser-javaplugin.so.
No alternatives for mozilla-javaplugin.so.
No alternatives for xulrunner-javaplugin.so.
Using '/usr/lib/jvm/java-6-sun/bin/appletviewer' to provide 'appletviewer'.
Using '/usr/lib/jvm/java-6-sun/bin/apt' to provide 'apt'.
Using '/usr/lib/jvm/java-6-sun/bin/extcheck' to provide 'extcheck'.
Using '/usr/lib/jvm/java-6-sun/bin/idlj' to provide 'idlj'.
Using '/usr/lib/jvm/java-6-sun/bin/jarsigner' to provide 'jarsigner'.
Using '/usr/lib/jvm/java-6-sun/bin/jar' to provide 'jar'.
Using '/usr/lib/jvm/java-6-sun/bin/javac' to provide 'javac'.
Using '/usr/lib/jvm/java-6-sun/bin/javadoc' to provide 'javadoc'.
Using '/usr/lib/jvm/java-6-sun/bin/javah' to provide 'javah'.
Using '/usr/lib/jvm/java-6-sun/bin/javap' to provide 'javap'.
Using '/usr/lib/jvm/java-6-sun/bin/jconsole' to provide 'jconsole'.
Using '/usr/lib/jvm/java-6-sun/bin/jdb' to provide 'jdb'.
Using '/usr/lib/jvm/java-6-sun/bin/jhat' to provide 'jhat'.
Using '/usr/lib/jvm/java-6-sun/bin/jinfo' to provide 'jinfo'.
Using '/usr/lib/jvm/java-6-sun/bin/jmap' to provide 'jmap'.
Using '/usr/lib/jvm/java-6-sun/bin/jps' to provide 'jps'.
Using '/usr/lib/jvm/java-6-sun/bin/jrunscript' to provide 'jrunscript'.
Using '/usr/lib/jvm/java-6-sun/bin/jsadebugd' to provide 'jsadebugd'.
Using '/usr/lib/jvm/java-6-sun/bin/jstack' to provide 'jstack'.
Using '/usr/lib/jvm/java-6-sun/bin/jstatd' to provide 'jstatd'.
Using '/usr/lib/jvm/java-6-sun/bin/jstat' to provide 'jstat'.
Using '/usr/lib/jvm/java-6-sun/bin/native2ascii' to provide 'native2ascii'.
Using '/usr/lib/jvm/java-6-sun/bin/rmic' to provide 'rmic'.
Using '/usr/lib/jvm/java-6-sun/bin/schemagen' to provide 'schemagen'.
Using '/usr/lib/jvm/java-6-sun/bin/serialver' to provide 'serialver'.
Using '/usr/lib/jvm/java-6-sun/bin/wsgen' to provide 'wsgen'.
Using '/usr/lib/jvm/java-6-sun/bin/wsimport' to provide 'wsimport'.
Using '/usr/lib/jvm/java-6-sun/bin/xjc' to provide 'xjc'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/jexec' to provide 'jexec'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide 'policytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so

Any help eliminating the error would be appreciated.

---

### Post by bakom on 2010-05-05
Hello,

I have the same problem as the threadstarter. I tried:

```

sudo update-java-alternatives -s java-6-openjdk

```

But I still get the following error, when trying to compile a java file (C-c C-v C-c)
```

Debugger entered--Lisp error: (error "Cannot find JDK's tools jar file (or equivalent).Type M-x describe-function [RET] jde-get-jdk-dir for more info.")
  signal(error ("Cannot find JDK's tools jar file (or equivalent).Type M-x describe-function [RET] jde-get-jdk-dir for more info."))
  error("Cannot find JDK's tools jar file (or equivalent).Type M-x describe-function [RET] jde-get-jdk-dir for more info.")
  jde-get-tools-jar()
  jde-bsh([object jde-bsh "JDEE BeanShell" [object jde-bsh-buffer "JDEE bsh buffer" "*JDEE bsh*" #<buffer *JDEE bsh*> unbound unbound] nil (lambda (&rest --cl-rest--) (apply #[... "rÃ!qÄ	J\n#)" [process G68101 output process-buffer bsh-snag-lisp-output] 4] ... --cl-rest--)) (lambda (&rest --cl-rest--) (apply #[... "rÃ!qÄ	J\n#)" [process G68102 output process-buffer bsh-snag-and-eval-lisp-output] 4] ... --cl-rest--)) (lambda (&rest --cl-rest--) (apply #[... "rÃ!qÄ	J\n#)" [process G68103 output process-buffer bsh-redirect-eval-output] 4] ... --cl-rest--)) "" "" "/usr/bin/java" nil "" unbound "/home/basil/emacs/addons/jdee/java/lib/bsh.jar" "bsh.Interpreter" nil "/home/basil/emacs/addons/jdee/java/bsh-commands" "/home/basil/emacs/addons/jdee/java/lib/checkstyle-all.jar" "/home/basil/emacs/addons/jdee/java/lib/jakarta-regexp.jar" "/home/basil/emacs/addons/jdee/java/lib/jde.jar" "/home/basil/emacs/addons/jdee/java/classes"])
  apply(jde-bsh [object jde-bsh "JDEE BeanShell" [object jde-bsh-buffer "JDEE bsh buffer" "*JDEE bsh*" #<buffer *JDEE bsh*> unbound unbound] nil (lambda (&rest --cl-rest--) (apply #[... "rÃ!qÄ	J\n#)" [process G68101 output process-buffer bsh-snag-lisp-output] 4] ... --cl-rest--)) (lambda (&rest --cl-rest--) (apply #[... "rÃ!qÄ	J\n#)" [process G68102 output process-buffer bsh-snag-and-eval-lisp-output] 4] ... --cl-rest--)) (lambda (&rest --cl-rest--) (apply #[... "rÃ!qÄ	J\n#)" [process G68103 output process-buffer bsh-redirect-eval-output] 4] ... --cl-rest--)) "" "" "/usr/bin/java" nil "" unbound "/home/basil/emacs/addons/jdee/java/lib/bsh.jar" "bsh.Interpreter" nil "/home/basil/emacs/addons/jdee/java/bsh-commands" "/home/basil/emacs/addons/jdee/java/lib/checkstyle-all.jar" "/home/basil/emacs/addons/jdee/java/lib/jakarta-regexp.jar" "/home/basil/emacs/addons/jdee/java/lib/jde.jar" "/home/basil/emacs/addons/jdee/java/classes"])
  eieio-generic-call(bsh-launch ([object jde-bsh "JDEE BeanShell" [object jde-bsh-buffer "JDEE bsh buffer" "*JDEE bsh*" #<buffer *JDEE bsh*> unbound unbound] nil (lambda ... ...) (lambda ... ...) (lambda ... ...) "" "" "/usr/bin/java" nil "" unbound "/home/basil/emacs/addons/jdee/java/lib/bsh.jar" "bsh.Interpreter" nil "/home/basil/emacs/addons/jdee/java/bsh-commands" "/home/basil/emacs/addons/jdee/java/lib/checkstyle-all.jar" "/home/basil/emacs/addons/jdee/java/lib/jakarta-regexp.jar" "/home/basil/emacs/addons/jdee/java/lib/jde.jar" "/home/basil/emacs/addons/jdee/java/classes"]))
  bsh-launch([object jde-bsh "JDEE BeanShell" [object jde-bsh-buffer "JDEE bsh buffer" "*JDEE bsh*" #<buffer *JDEE bsh*> unbound unbound] nil (lambda (&rest --cl-rest--) (apply #[... "rÃ!qÄ	J\n#)" [process G68101 output process-buffer bsh-snag-lisp-output] 4] ... --cl-rest--)) (lambda (&rest --cl-rest--) (apply #[... "rÃ!qÄ	J\n#)" [process G68102 output process-buffer bsh-snag-and-eval-lisp-output] 4] ... --cl-rest--)) (lambda (&rest --cl-rest--) (apply #[... "rÃ!qÄ	J\n#)" [process G68103 output process-buffer bsh-redirect-eval-output] 4] ... --cl-rest--)) "" "" "/usr/bin/java" nil "" unbound "/home/basil/emacs/addons/jdee/java/lib/bsh.jar" "bsh.Interpreter" nil "/home/basil/emacs/addons/jdee/java/bsh-commands" "/home/basil/emacs/addons/jdee/java/lib/checkstyle-all.jar" "/home/basil/emacs/addons/jdee/java/lib/jakarta-regexp.jar" "/home/basil/emacs/addons/jdee/java/lib/jde.jar" "/home/basil/emacs/addons/jdee/java/classes"])
  jde-compile-compiler([object jde-compile-javac-16 "javac 1.6.x" unbound "1.6" unbound [object jde-compile-server-buffer "compilation buffer" "*JDEE Compile Server*" #<buffer *JDEE Compile Server*> nil (lambda ... ...)] #<window 6 on *JDEE Compile Server*> nil t])
  apply(jde-compile-compiler [object jde-compile-javac-16 "javac 1.6.x" unbound "1.6" unbound [object jde-compile-server-buffer "compilation buffer" "*JDEE Compile Server*" #<buffer *JDEE Compile Server*> nil (lambda ... ...)] #<window 6 on *JDEE Compile Server*> nil t])
  eieio-generic-call(jde-compile-run-server ([object jde-compile-javac-16 "javac 1.6.x" unbound "1.6" unbound [object jde-compile-server-buffer "compilation buffer" "*JDEE Compile Server*" #<buffer *JDEE Compile Server*> nil ...] #<window 6 on *JDEE Compile Server*> nil t]))
  jde-compile-run-server([object jde-compile-javac-16 "javac 1.6.x" unbound "1.6" unbound [object jde-compile-server-buffer "compilation buffer" "*JDEE Compile Server*" #<buffer *JDEE Compile Server*> nil (lambda ... ...)] #<window 6 on *JDEE Compile Server*> nil t])
  jde-compile-compiler([object jde-compile-javac-16 "javac 1.6.x" unbound "1.6" unbound [object jde-compile-server-buffer "compilation buffer" "*JDEE Compile Server*" #<buffer *JDEE Compile Server*> nil (lambda ... ...)] #<window 6 on *JDEE Compile Server*> nil t])
  apply(jde-compile-compiler [object jde-compile-javac-16 "javac 1.6.x" unbound "1.6" unbound [object jde-compile-server-buffer "compilation buffer" "*JDEE Compile Server*" #<buffer *JDEE Compile Server*> nil (lambda ... ...)] #<window 6 on *JDEE Compile Server*> nil t])
  eieio-generic-call(jde-compile-launch ([object jde-compile-javac-16 "javac 1.6.x" unbound "1.6" unbound [object jde-compile-server-buffer "compilation buffer" "*JDEE Compile Server*" #<buffer *JDEE Compile Server*> nil ...] #<window 6 on *JDEE Compile Server*> nil t]))
  jde-compile-launch([object jde-compile-javac-16 "javac 1.6.x" unbound "1.6" unbound [object jde-compile-server-buffer "compilation buffer" "*JDEE Compile Server*" #<buffer *JDEE Compile Server*> nil (lambda ... ...)] #<window 6 on *JDEE Compile Server*> nil t])
  jde-compile-compiler([object jde-compile-javac-16 "javac 1.6.x" unbound "1.6" unbound [object jde-compile-server-buffer "compilation buffer" "*JDEE Compile Server*" #<buffer *JDEE Compile Server*> nil (lambda ... ...)] #<window 6 on *JDEE Compile Server*> nil t])
  apply(jde-compile-compiler [object jde-compile-javac-16 "javac 1.6.x" unbound "1.6" unbound [object jde-compile-server-buffer "compilation buffer" "*JDEE Compile Server*" #<buffer *JDEE Compile Server*> nil (lambda ... ...)] #<window 6 on *JDEE Compile Server*> nil t])
  eieio-generic-call(jde-compile-compile ([object jde-compile-javac-16 "javac 1.6.x" unbound "1.6" unbound [object jde-compile-server-buffer "compilation buffer" "*JDEE Compile Server*" #<buffer *JDEE Compile Server*> nil ...] #<window 6 on *JDEE Compile Server*> nil t]))
  jde-compile-compile([object jde-compile-javac-16 "javac 1.6.x" unbound "1.6" unbound [object jde-compile-server-buffer "compilation buffer" "*JDEE Compile Server*" #<buffer *JDEE Compile Server*> nil (lambda ... ...)] #<window 6 on *JDEE Compile Server*> nil t])
  jde-compile()
  call-interactively(jde-compile nil nil)

```

Any help is appreciated! :-)

---

