---
title: "Evolution and non ASCII storage"
date: 2013-04-11
forum: Programming Talk
---

### Post by kaspar_silas on 2013-04-11
I have an evolution filter that puts certain emails into a sub folder. Background programs then watch the associated folder 
( /home/Name/.local/share/evolution/mail/local/.Queue/cur )
and when an email arrives they process the information contained in the emails. You have to decode the stored email but it is normally pretty easy as most of the header is normally in plain ASCII (attachments are base64 encoded first). The problem is the subject line. Sometimes this is plain ASCII like:

Subject: NISTXRAYREQ Thorium -pscaled

but sometimes it's in this form:

=?windows-1256?Q?NISTXRAYRE?= =?windows-1256?Q?Q_u_-pscal?=
 =?windows-1256?Q?ed=FE?=

or this form:

Subject: =?utf-8?B?TklTVFhSQVlSRVEgSXJvbiAtcHNjYWxlZA==?=

Dependent on the client that sent the email. Now I am guessing these are some sort of alternative to ASCII used to cope with extended character sets. Does anyone know if this is right and ideally how to convert these lines into ASCII?

O and I do know you can call a program from evolution. However I do quite a bit of processing on the email contents sometimes using bits from multiple emails so it's a lot easier to do this all outside evolution.

---

### Post by schragge on 2013-04-11
The ?Q? strings are in [quoted-printable]("http://en.wikipedia.org/wiki/Quoted-printable"). You can decode it with [qprint]("http://manpages.ubuntu.com/manpages/quantal/en/man1/qprint.1.html").
The ?B? strings are in [base64]("http://en.wikipedia.org/wiki/Base64"). Decode it with [base64]("http://manpages.ubuntu.com/manpages/quantal/en/man1/base64.1.html").

Or do it with perl
```

[COLOR=green]$[/COLOR] perl -mEncode=decode -ne 'print decode("MIME-Header",$_)."\n"' <<<'=?windows-1256?Q?NISTXRAYRE?= =?windows-1256?Q?Q_u_-pscal?=  =?windows-1256?Q?ed?='
[COLOR=green]NISTXRAYREQ u -pscaled
$[/COLOR] perl -mEncode=decode -ne 'print decode("MIME-Header",$_)."\n"' <<<'Subject: =?utf-8?B?TklTVFhSQVlSRVEgSXJvbiAtcHNjYWxlZA==?='
[COLOR=green]Subject: NISTXRAYREQ Iron -pscaled[/COLOR]

```

---

### Post by kaspar_silas on 2013-04-12
Excellent and thanks that makes perfect sense. 
(As most things do when someone tells you the answer)

---

