---
title: "[SOLVED] [HELP]Ocsigen"
date: 2008-05-24
forum: Programming Talk
---

### Post by Kadrus on 2008-05-24
Hello everyone.I am having a little problem running Ocsigen server under Ubuntu..I don't know how many of you have heard of it but its a web server developed with Objective Caml..[LINK]("http://ocsigen.org/")
I have most of the Ocaml packages installed..and Ocsigen also installed..I happen to be running Apache on localhost port 80..so i changed the port of the ocsigen config script so they can run as reverse proxy..but no luck..
in my /var/www/ directory..i have the Ocsigen folder including its file which are the wiki example developed with Ocaml(Ocsigen,Eliom)if i am not mistaken..(nurpawiki)...so i think everything is installed..now when i type in Terminal ocsigen to start the server as mentionned in the doc manual at the website [Ocsigen]("http://www.ocsigen.org") i get this :```
No bytecode file specified.

```
so i try another way to start the server using :```
sudo /etc/init.d/ocsigen start
```
i get ```
Configuration file prevent ocsigen to be started (use force-start).
```
so im thinking that there is something wrong with my config file but i have configured following the steps on the website..so I'm confused..
here's my config file:
```

<ocsigen>
    <!-- Each <server> tag describes a different server process: 
	they must listen on different ports 
    -->
  <server>
    <port>127.0.1.1:8080</port> <!-- The port for the server -->
    <!-- <port protocol="HTTPS">443</port> You can listen on several port, and protocol may be HTTP (default) or HTTPS -->
    <logdir>/var/log/ocsigen</logdir> <!-- Where log files are to be written -->
    <staticdir>/var/www/ocsigen</staticdir> <!-- Where static pages are (default: none) -->
    <datadir>/var/lib/ocsigen</datadir> <!-- Where data are (default: /var/lib/ocsigen) -->
    <user>ocsigen</user> <!-- The user who will run Ocsigen (not root!) -->
    <group>ocsigen</group> <!-- The group (not root!) -->

    <charset>utf-8</charset> <!-- Default charset for pages -->
    <!-- uploaddir></uploaddir --> <!-- Where files are to be downloaded (default: none) -->
    <!-- maxuploadfilesize>2Mo</maxuploadfilesize --> <!-- Max size of files sent to the server ("infinity" or using SI or binary units, e.g. 10 10B 10o 10ko 10kB 10kiB 10MiB 10TB ...) -->
    <!-- maxrequestbodysize>8Mo</maxrequestbodysize --> <!-- Max size for the body of a request ("infinity" or using SI or binary units) -->
    <!--<mimefile>/etc/mime.types</mimefile> The mime types file 
                          used for sending static pages -->
    <!-- <debugmode/> If you want to print the exceptions on error 500 pages (use only for debug) -->

    <!-- If you want to use HTTPS:
    <ssl>
       <certificate>path_to/cert.pem</certificate>
       <privatekey>path_to/privkey.pem</privatekey>
    </ssl>

    To create a 1024-bit private key to use when creating your CA.:
    openssl genrsa -des3 -out privkey.pem 1024

    To create a master certificate based on this key, to use when signing other
    certificates:
    openssl req -new -x509 -days 1001 -key privkey.pem -out cert.pem

    If you don't want to be asked for a password at start-up, you can
    uncrypt the private key (if you consider it is safe ...):
    openssl rsa -in privkey.pem -out privkey-unsec.pem

    -->

    <!-- Ocsigen extensions.
         Dynlink here all the extensions for Ocsigen.
         Warning: The order in important! (as they will try to handle
         requests in that order)
         (for example a proxy extension must be loaded before all page
         generating extensions, as it catches the request before it is
         fully read)
         You probably need staticmod and eliom, in that order,
         the first one to generate static pages,
         the second one for dynamic pages.
         If you don't have any extension, no page will be generated
         (but if you link the extensions statically).
     -->
    <extension module="/usr/lib/ocaml/3.09.2/ocsigen/staticmod.cmo"/>
    <extension module="/usr/lib/ocaml/3.09.2/ocsigen/eliom.cma"/>

    <!-- Eliom has the following options:
    <extension module="/usr/lib/ocaml/3.09.2/ocsigen/eliom.cma">
      <timeout value="7200"/> <!-- Thus, the default timeout for sessions is
                                   2 hours.
                                   value="infinity" means that the session will
                                   never finish.
                                   Note that each eliom module may set its own
                                   default, that will override this one. -->
      <persistenttimeout value="7200"/> <!--Idem for persistent session data-->
      <sessiongcfrequency value="7200"/> <!-- Time between two garbage
                                   collections of sessions, in seconds (default
                                   3600) "infinity" means no GC of session -->
      <persistentsessiongcfrequency value="86400"/> <!-- Time between two
                                   garbage collections of persistent sessions, 
                                   in seconds (default 86400.) "infinity" 
                                   means no GC of session -->
      <!-- The following two are Ocsipersist parameters
        Ocsipersist is a library for persistent data included in eliom.cma.
        You can use it even if you don't use eliom.cma
        by dynlinking ocsipersist.cma -->
      <store dir="/var/lib/ocsigen"/> <!-- The directory for data -->
      <ocsidbm name="/usr/bin/ocsidbm"/> <!-- The data server process -->
    </extension>
    -->



    <!-- For compatibility with sites developped with old versions (< 0.7): -->
    <!-- extension module="/usr/lib/ocaml/3.09.2/ocsigen/ocsigenmod.cma"/ -->

    <!-- If Ocsigen is compiled with Ocamlduce support, 
        and you want to use it, add:
    <extension module="...PATH TO.../ocamlduce.cma"/>
    <extension module="/usr/lib/ocaml/3.09.2/ocsigen/eliomduce.cma"/>
    -->

    <!-- If you want to load other Ocaml modules, either use
    <extension module="...PATH TO.../toto.cma"/>
    if you don't want them to be reloaded when you reload dynamically the sites
        or
    <library module="...PATH TO.../toto.cma"/>
    if you want them to be reloaded

    Extensions like eliom.cma or staticmod.cmo cannot be used with <library>
    (as the server is trying extensions in the order they are loaded)
    -->

    <host>  
      <!-- Now attach each Eliom module to an URL 
           (and possibly to a directory for its static pages) -->
      <site dir="" charset="iso-8859-1"> 
        <!-- dir is the directory where the site is loaded -->
        <!-- charset is optional -->
        <!-- Tutorial -->
        <eliom module="/usr/lib/ocsigen/tutoeliom.cmo" />
        <static dir="/var/www/ocsigen/tutorial" />
      </site>


      <site dir="nurpawiki" charset="utf-8">
        <eliom module="/usr/lib/ocsigen/nurpawiki.cmo">
          <!-- Where to store Wiki pages -->
          <wikidata dir="/var/lib/ocsigen/nurpawiki"/>
        </eliom>
        <static dir="/var/www/ocsigen/nurpawiki" />
      </site>

      <!-- Rewriting URLs:
      <site dir="" charset="utf-8">
        <static regexp="~([^/]*)(.*)" dest="/home/$1/public_html$2"/>
        <!-- The syntax of regular expression is PCRE's one -->
        <!-- Better: if your users are not all in the same directory: -->
        <static regexp="~([^/]*)(.*)" dest="$$u($1)/public_html$2"/>
      </site>
      -->



      <!-- If Ocsigen is compiled with Ocamlduce support, 
        you may add:
      <site dir="duce" charset="iso-8859-1"> 
        <eliom module="/usr/lib/ocsigen/exampleduce.cmo" />
      </site>
        Warning: exampleduce.cmo depends on tutorial.cmo 
        (must be dynlinked before)!
      -->

      <!--
      <site dir="monitoring">
        <!-- Monitoring -->
        <eliom module="/usr/lib/ocsigen/monitoring.cmo" />
      </site>
      -->
    </host>

    <!-- 
    <host name="*.com">
    </host>

       If your server has several host names, you can decide which sites will
       be available for each name, using virtual servers.
       To use virtual servers, specify for <host> the attribute 'name'.
       'name' is a string that may contain '*' characters.
       Examples: <host name="*">...</host> will match any host name (default).
       <host name="*.com:80">...</host> will match any host name finishing 
       with '.com' on port 80.
       <host name="www.mysite.com www.mysite.org:*">...</host> 
	will match only those two hostnames.
     -->
  

    <!-- Change the following values only if you know what you are doing! -->
    <!-- <maxconnected>500</maxconnected> Max number of simultaneous connections -->
    <!-- <timeout>20</timeout> Timeout for connections -->
    <!-- <keepalivetimeout>10</keepalivetimeout> Amount of time the server will wait for subsequent requests on a persistent connection -->
    <!-- <netbuffersize>8192</netbuffersize> Size of the input buffer (sockets) It is also the maximum size of headers and post data (version 0.5.0) -->
    <!-- <filebuffersize>8192</filebuffersize> Size of the buffer for reading files -->
    <!-- <minthreads>10</minthreads> Minimum size of the detached threads pool (default 10) -->
    <!-- <maxthreads>1000</maxthreads> Maximal size of the detached threads pool (default 300) -->
    <!-- <maxdetachedcomputationsqueued>100</maxdetachedcomputationsqueued> Size of the queue of computations waiting a detached thread (default 100) -->
    <!-- commandpipe>/var/run/ocsigen_command</commandpipe --> <!-- Name of the pipe used to command the server -->

  </server>
  
</ocsigen>

```
So any help will be greatly appreciated. :)

---

### Post by vincent.balat on 2008-06-02
Hi,

Debian does not launch Ocsigen by default. To activate it, you just need to change the variable LAUNCH_AT_STARTUP in file /etc/default/ocsigen

For other questions about Ocsigen, you may want to register to Ocsigen's mailing list. (see [http://ocsigen.org](http://ocsigen.org) )

Cheers,
Vincent Balat

---

### Post by Kadrus on 2008-06-02
thanks a lot for the help :-)..doesn't get better than the project leader helping you out:p:)

---

