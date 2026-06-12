---
title: "c++ cout to a FILE* ~ how do I."
date: 2011-04-23
forum: Programming Talk
---

### Post by highspider on 2011-04-23
how to write to a FILE* with << or cout << 
[COLOR=Blue]all I really need is cout for popen().[/COLOR]

```

[COLOR=Blue]FILE *[/COLOR]mail;
mail =[COLOR=Blue] [/COLOR][COLOR=Blue]popen[/COLOR] ("/usr/sbin/sendmail -t", "w");
  fprintf (mail, "To: %s\n", Self_ID );
  [COLOR=Red]fprintf (mail, "From: %s\n", dataString.substr(Semailloc, Eemailloc - Semailloc) );[/COLOR]
  fprintf (mail, "Subject: %s\n", Subject);
  fprintf (mail, "\n");
[COLOR=Red]  fprintf (mail, "%s", dataString.substr(Smsgloc, Emsgloc - Smsgloc) );[/COLOR]
  fprintf (mail, "\n.\n");

```

readlines don't work

---

### Post by james_mcl on 2011-04-23
Have you tried C++ style file handling?

```

std::string infile = "/usr/sbin/sendmail -t";
//I admit I'm not sure how the code's going to handle that -t in the
//filename.
//So this may require someone smarter than me.

std::ofstream fout(infile.c_str(), std::ios::out);
if (!fout)
{
    //it didn't open the file, do some error-handling.
}
else
{
  fout<<"To: "<<Self_ID<<"\n";
  fout<<"From: "<<dataString.substr(Semailloc, Eemailloc - Semailloc)<<"\n";
  fout<<"Subject: "<<Subject<<"\n";
  fout<<"\n";
  fout<<dataString.substr(Smsgloc, Emsgloc - Smsgloc);
  fout<<"\n.\n";
}
```

---

### Post by james_mcl on 2011-04-23
I should really have called that "outfile", rather than "infile". Oh well...

---

### Post by ve4cib on 2011-04-23
A few questions if I might...

You can confirm that the black lines do work though?

What are the contents of the file/stream when you run your code?

If you change the FILE* to be a plain text file does it work then?


My first reaction is that the problem may be with your substr calls.  If they're not returning anything -- or returning the wrong thing -- that could be causing errors in the output.

---

### Post by highspider on 2011-04-23
> **ve4cib said:**
> A few questions if I might...

You can confirm that the black lines do work though?

What are the contents of the file/stream when you run your code?

If you change the FILE* to be a plain text file does it work then?


My first reaction is that the problem may be with your substr calls.  If they're not returning anything -- or returning the wrong thing -- that could be causing errors in the output.

[COLOR=Red]yes [/COLOR]the whole program does work with strings.
  just not [COLOR=RoyalBlue]dataString.substr() [/COLOR]with fprintf.

and this debug works 100% also.
```

cout   << "<p>" << contentLength << "</p>"
         << "<p>dataString:" << dataString << "</p>"
         << "<br />Snameloc:" << Snameloc
         << "<br />Enameloc:" << Enameloc << "<br />"
         <<  dataString.substr(Snameloc, Enameloc - Snameloc)
         << "<br />Semailoc:" << Semailloc
         << "<br />Eemailoc:" << Eemailloc << "<br />"
         << dataString.substr(Semailloc, Eemailloc - Semailloc)
         << "<br />Sphoneloc:" << Sphoneloc
         << "<br />Ephoneloc:" << Ephoneloc << "<br />"
         <<  dataString.substr(Sphoneloc, Ephoneloc - Sphoneloc)
         << "<br />Smsgloc:" << Smsgloc
         << "<br />Emsgloc:" << Emsgloc << "<br />"
         << dataString.substr(Smsgloc, Emsgloc - Smsgloc) << endl;

```

---

### Post by ve4cib on 2011-04-23
The substr function returns a string object, not a char*.  The "%s" placeholder in fprintf expects a pointer to a char with a null terminator somewhere, not a string object.  That could be what's causing your problem.

---

### Post by highspider on 2011-04-23
solved with .c_str() thanks [james_mcl]("http://ubuntuforums.org/member.php?u=247099")
```

 mail = popen (MAIL_PROGRAM, "w");
        fprintf (mail, "To: %s\n", Self_ID );
        fprintf (mail, "From: %s\n", dataString.substr(Snameloc, Enameloc - Snameloc).[COLOR=Red]c_str()[/COLOR] );
        fprintf (mail, "Subject: %s\n", Subject);
        fprintf (mail, "\n");
        fprintf (mail, "Name [%s]\nEmail [%s]\nPhone [%s]\n\n%s",dataString.substr(Snameloc, Enameloc - Snameloc)[COLOR=Red].c_str[/COLOR](),
                                                                 dataString.substr(Semailloc, Eemailloc - Semailloc)[COLOR=Red].c_str()[/COLOR],
                                                                 dataString.substr(Sphoneloc, Ephoneloc - Sphoneloc)[COLOR=Red].c_str()[/COLOR],
                                                                 dataString.substr(Smsgloc, Emsgloc - Smsgloc)[COLOR=Red].c_str()[/COLOR] );
        fprintf (mail, "\n.\n");
        pclose (mail);

```

---

