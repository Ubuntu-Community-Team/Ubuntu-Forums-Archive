---
title: "Problems with date cmd in terminal"
date: 2006-06-28
forum: Programming Talk
---

### Post by Browser_ice on 2006-06-28
I am currently geting back to writing shell scripts. I am a bit rusty.

I am having problems with the date command. I am simply trying to store the date inside a variable. But to achieve this, I am playing with this command on the console with different options. One of which, doesn't seam to work. But according to its --help, it should. What am I doing wrong ?

browserice@Linux:~$ date --help
Usage: date [OPTION]... [+FORMAT]
  or:  date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]
Display the current time in the given FORMAT, or set the system date.

  -d, --date=STRING         display time described by STRING, not `now'
...

browserice@Linux:~$ date -d=%d/%m/%y
date: invalid date `=%d/%m/%y'
browserice@Linux:~$ date -d='%d/%m/%y'
date: invalid date `=%d/%m/%y'
browserice@Linux:~$ date -d="%d/%m/%y"
date: invalid date `=%d/%m/%y'
browserice@Linux:~$ date -d '%d%m%y'
date: invalid date `%d%m%y'
browserice@Linux:~$ date --date='%d/%m/%y'
date: invalid date `%d/%m/%y'
browserice@Linux:~$ date --date='%d%m%y'
date: invalid date `%d%m%y'

---

### Post by wmcbrine on 2006-06-28
-d lets you specify a different time, not a different format.

What you're looking for is '+'.

wmcbrine@alanis:~$ date +%d/%m/%y
28/06/06
wmcbrine@alanis:~$ date -d tomorrow
Thu Jun 29 15:47:42 EDT 2006

---

### Post by Browser_ice on 2006-06-28
Then why does the "man date" specifies otherwise ?

Is there a problem of command description versions in the "man" cmd ?
[SIZE="1"][INDENT]
NAME
       date - print or set the system date and time

SYNOPSIS
       date [OPTION]... [+FORMAT]
       date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]

DESCRIPTION
       Display the current time in the given FORMAT, or set the system date.

       [B]-d, --date=STRING
              display time described by STRING, not &#8216;now&#8217;[/B]

       -f, --file=DATEFILE
              like --date once for each line of DATEFILE

       -r, --reference=FILE
              display the last modification time of FILE

       -R, --rfc-2822
              output date and time in RFC 2822 format

       --rfc-3339=TIMESPEC
              output date and time in RFC 3339 format.  TIMESPEC=&#8216;date&#8217;, &#8216;sec&#8208;
              onds&#8217;, or &#8216;ns&#8217; for date and time to the indicated precision.

       -s, --set=STRING
              set time described by STRING

       -u, --utc, --universal
              print or set Coordinated Universal Time

       --help display this help and exit

       --version
              output version information and exit

       FORMAT controls the output.  The only valid option for the second  form
       specifies Coordinated Universal Time.  Interpreted sequences are:

       %%     a literal %

       %a     locale&#8217;s abbreviated weekday name (e.g., Sun)

       %A     locale&#8217;s full weekday name (e.g., Sunday)

       %b     locale&#8217;s abbreviated month name (e.g., Jan)

       %B     locale&#8217;s full month name (e.g., January)

       %c     locale&#8217;s date and time (e.g., Thu Mar  3 23:05:25 2005)

       %C     century; like %Y, except omit last two digits (e.g., 21)

       %d     day of month (e.g, 01)

       %D     date; same as %m/%d/%y

       %e     day of month, space padded; same as %_d

       %F     full date; same as %Y-%m-%d

       %g     the  last  two  digits  of the year corresponding to the %V week
              number

       %G     the year corresponding to the %V week number

       %h     same as %b

       %H     hour (00..23)

       %I     hour (01..12)

       %j     day of year (001..366)

       %k     hour ( 0..23)

       %l     hour ( 1..12)

       %m     month (01..12)

       %M     minute (00..59)

       %n     a newline

       %N     nanoseconds (000000000..999999999)

       %p     locale&#8217;s equivalent of either AM or PM; blank if not known

       %P     like %p, but lower case

       %r     locale&#8217;s 12-hour clock time (e.g., 11:11:04 PM)

       %R     24-hour hour and minute; same as %H:%M

       %s     seconds since 1970-01-01 00:00:00 UTC

       %S     second (00..60)

       %t     a tab

       %T     time; same as %H:%M:%S

       %u     day of week (1..7); 1 is Monday

       %U     week number of year with Sunday as first day of week (00..53)

       %V     week number of year with Monday as first day of week (01..53)

       %w     day of week (0..6); 0 is Sunday

       %W     week number of year with Monday as first day of week (00..53)

       %x     locale&#8217;s date representation (e.g., 12/31/99)

       %X     locale&#8217;s time representation (e.g., 23:13:48)

       %y     last two digits of year (00..99)

       %Y     year

       %z     +hhmm numeric timezone (e.g., -0400)

       %:z    +hh:mm numeric timezone (e.g., -04:00)

              %::z +hh:mm:ss numeric time zone (e.g., -04:00:00) %:::z numeric
              time  zone  with : to necessary precision (e.g., -04, +05:30) %Z
              alphabetic time zone abbreviation (e.g., EDT)

       By default, date  pads  numeric  fields  with  zeroes.   The  following
       optional flags may follow &#8216;%&#8217;:

              - (hyphen) do not pad the field _ (underscore) pad with spaces 0
              (zero) pad with zeros ^ use upper case if possible #  use  oppo&#8208;
              site case if possible

       After  any  flags  comes  an optional field width, as a decimal number;
       then an optional modifier, which is either E to use the locale&#8217;s alter&#8208;
       nate  representations  if available, or O to use the locale&#8217;s alternate
       numeric symbols if available.

AUTHOR
       Written by David MacKenzie.

REPORTING BUGS
       Report bugs to <bug-coreutils@gnu.org>.

COPYRIGHT
       Copyright © 2005 Free Software Foundation, Inc.
       This is free software.  You may redistribute copies  of  it  under  the
       terms       of       the      GNU      General      Public      License
       <http://www.gnu.org/licenses/gpl.html>.  There is NO WARRANTY,  to  the
       extent permitted by law.

SEE ALSO
       The  full documentation for date is maintained as a Texinfo manual.  If
       the info and date programs are properly installed  at  your  site,  the
       command

              info date

       should give you access to the complete manual.[/INDENT][/SIZE]

---

### Post by wmcbrine on 2006-06-28
[QUOTE=Browser_ice]Then why does the "man date" specifies otherwise ?[/QUOTE]It doesn't. You're misreading it.

---

### Post by Arndt on 2006-06-29
[QUOTE=Browser_ice]I am currently geting back to writing shell scripts. I am a bit rusty.

I am having problems with the date command. I am simply trying to store the date inside a variable. But to achieve this, I am playing with this command on the console with different options. One of which, doesn't seam to work. But according to its --help, it should. What am I doing wrong ?

browserice@Linux:~$ date --help
Usage: date [OPTION]... [+FORMAT]
  or:  date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]
Display the current time in the given FORMAT, or set the system date.

  -d, --date=STRING         display time described by STRING, not `now'
...

browserice@Linux:~$ date -d=%d/%m/%y
date: invalid date `=%d/%m/%y'
browserice@Linux:~$ date -d='%d/%m/%y'
date: invalid date `=%d/%m/%y'
browserice@Linux:~$ date -d="%d/%m/%y"
date: invalid date `=%d/%m/%y'
browserice@Linux:~$ date -d '%d%m%y'
date: invalid date `%d%m%y'
browserice@Linux:~$ date --date='%d/%m/%y'
date: invalid date `%d/%m/%y'
browserice@Linux:~$ date --date='%d%m%y'
date: invalid date `%d%m%y'[/QUOTE]

"date --help" says, among other things (and I _hate_ programs which react to -h by just telling me to use --help)
```
  -d, --date=STRING         display time described by STRING, not `now'
```

Here are some examples:

```
$ date --date=2004-05-06
Thu May  6 00:00:00 CEST 2004
$ date -d 2004-05-06
Thu May  6 00:00:00 CEST 2004
$ date -d=2004-05-06
date: invalid date `=2004-05-06'
$ date -d 05/06/04
Thu May  6 00:00:00 CEST 2004
$ date -d05/06/04
Thu May  6 00:00:00 CEST 2004
```

I might also misunderstand the description "time described by STRING", but when they contrast it with "now", I think the description is OK.

By the way, note among the above examples that "-d=2004-05-06" is not correct usage. It's usually only the -- options that use the equals sign. The older - options mostly do not.

---

### Post by FroL_Onn on 2013-03-20
> **wmcbrine said:**
> -d lets you specify a different time, not a different format.

What you're looking for is '+'.

wmcbrine@alanis:~$ date +%d/%m/%y
28/06/06
wmcbrine@alanis:~$ date -d tomorrow
Thu Jun 29 15:47:42 EDT 2006
Thanks a lot! This helped me!)

---

### Post by howefield on 2013-03-20
Old thread closed.

---

