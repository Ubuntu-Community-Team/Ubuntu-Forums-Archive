---
title: "kmymoney2 from cvs"
date: 2006-01-05
forum: Packaging and Compiling Programs
---

### Post by rjwood on 2006-01-05
I am configureing this program and am stuck here:

2)   Run configure to tell the project about your local environment

           ./configure --with-qt-dir=[your location of qt3] \
                       --prefix=[your location of kde3]

     Below, please find a table of values for the above for several
     distributions:

     Distribution      | --with-qt-dir           | --prefix
     ------------------+-------------------------+---------------------------
     SuSE >= 8.1       |  omit this parameter    | ommit this parameter
     Mandrake 9.0      |  omit this parameter    | /usr
     Slackware >= 9.0  |  omit this parameter    | /opt/kde
     MEPIS             |  omit this parameter    | /usr
     RedHat 8/9        |  omit this parameter    | /usr
     Fedora 1/2           |  omit this parameter    | /usr
     Mandriva 2006     |  omit this parameter    | /usr
     
     Distribution      | --man-dir               | --program-prefix
     ------------------+-------------------------+---------------------------
     SuSE >= 8.1       |  /usr/share/man         | omit this parameter
     Mandrake 9.0      |  ???                    | 
     Slackware >= 9.0  |  /usr/share/man         | 
     MEPIS             |  omit this parameter    | omit this parameter
     Mandriva 2006     |  /usr/share/man         | /usr

     so for SuSE 9.1 the command is:

           ./configure --mandir=/usr/share/man 

     Please tell us the values for other distributions, so we can add
     them to this list. Send an e-mail to the developers mailing list.
     See the address below.

Can anyone please direct me? 

FYI-- the version in syaptic, although the same v# lacks some recent feature upgrade that are important to me.

Thanks in advance!!

---

### Post by rjwood on 2006-01-14
somebody please give me a hand with this. I am beginning to feel unwanted as none of my questions are getting answered.;)

---

### Post by _graham_ on 2006-08-28
Try it with
./configure --prefix=/usr
Let us know how you get on.

---

