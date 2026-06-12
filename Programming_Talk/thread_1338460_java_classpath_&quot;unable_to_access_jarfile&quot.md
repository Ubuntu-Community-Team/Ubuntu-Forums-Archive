---
title: "java classpath &quot;unable to access jarfile&quot;"
date: 2009-11-26
forum: Programming Talk
---

### Post by candidoaramburu on 2009-11-26
Hi,

when i run $java -jar batik-squiggle.jar the error message on screen is
"unable to acces jarfile batik-squiggle.jar" and the path of the jar file is edited with the $CLASSPATH variable in the ~/.bash_profile

if i execute $java -jar /usr/share/batik-1.7/batik-squiggle.jar there is not problem

if i execute $java -cp /usr/share/batik-1.7/batik-squiggle.jar -jar batik-1.7.jar the error message is the above one.

the java virtual machine is sun jdk6

the application file is
-rw-r--r-- 1 root root 553671 2008-01-06 11:11 /usr/share/batik-1.7/batik-squiggle.jar

This is my .bash_profile file content

#Fichero de configuración que se ejecuta al:
#    entrar en SESION y
#    al ejecutar source ~/.bash_profile



#configuracion de imagemagick . /usr/bin ya esta en el path
export MAGICK_HOME="$HOME/imagemagick"
export LD_LIBRARY_PATH="/usr/lib"

#Configuración del PATH para:
#java,xmlmind editor
export PATH=$PATH:$JAVA_HOME/bin:/usr/share/xxe-perso-4_5_0/bin

#instalacion de la maquina virtual java-6-sun
#configuración de JAVA_HOME
export JAVA_HOME="/usr/lib/jvm/java-6-sun"
export JAR_HOME="/usr/share/java"

#configuracion de la validacion de documentos xml con saxon
export CLASSPATH=.:$JAVA_HOME/lib/tools.jar:$JAR_HOME/saxon.jar:$JAR_HOME/docbook-xsl-saxon.jar:$JAR_HOME/xercesImpl.jar

#configuracion para batik:
[B]export CLASSPATH=$CLASSPATH:/usr/share/batik-1.7/batik-squiggle.jar
[/B]

#configuración para xalan
export CLASSPATH=$CLASSPATH:$JAR_HOME/xalan2.jar:$JAR_HOME/xml-apis.jar:$JAR_HOME/docbook-website-xalan2.jar

#configuración para fop
export CLASSPATH=$CLASSPATH:$JAR_HOME/fop.jar:$JAR_HOME/avalon-framework.jar:$JAR_HOME/batik.jar:$JAR_HOME/commons-io.jar:$JAR_HOME/commons-logging.jar:$JAR_HOME/jai_core.jar:$JAR_HOME/jai_codec.jar:$JAR_HOME/fop-hyph.jar:$JAR_HOME/serializer.jar:$JAR_HOME/xmlgraphics-commons.jar


#configuracion para los samples de xeres apache. Synaptic no instala xercesSamples.jar
export CLASSPATH=$CLASSPATH:$JAR_HOME/xerces.jar:/usr/share/xerces-1_4_4/xercesSamples.jar

---

### Post by LKjell on 2009-11-26
-rw-r--r-- 1 root root 553671 2008-01-06 11:11 /usr/share/batik-1.7/batik-squiggle.jar

programs need execute to run.

---

### Post by pbrockway2 on 2009-11-26
> **LKjell said:**
> -rw-r--r-- 1 root root 553671 2008-01-06 11:11 /usr/share/batik-1.7/batik-squiggle.jar

programs need execute to run.

batik-squiggle.jar is a jar archive not a program.

@OP You need to specify the name of the jar file which contains the main class.  The classpath has nothing to do with this.

---

### Post by candidoaramburu on 2009-12-01
Hi,

I think that main class is "org/apache/batik/apps/svgbrowser/Main.class" in "batik-squiggle.jar" file

This is the content of batik-squiggle.jar file about Main-Class paremeter in the MANIFEST.MF file

root@izar:/usr/share/batik-1.7# jar xf batik-squiggle.jar META-INF/MANIFEST.MF && cat META-INF/MANIFEST.MF | grep Main-Class | awk '{ print $2}' 
org.apache.batik.apps.svgbrowser.Main
root@izar:/usr/share/batik-1.7# jar tf batik-squiggle.jar | grep org/apache/batik/apps/svgbrowser/Main.class
org/apache/batik/apps/svgbrowser/Main.class

so the $CLASSPATH is ok no?
Whats the configuration error?


Thanks

---

