---
title: "Please Help with Awk code"
date: 2012-01-28
forum: Programming Talk
---

### Post by JamesOwen on 2012-01-28
Hey guy’s,

I need help with this code, I am reading from a pipe I need to this code to read and parse the xml file that I have for 2 minutes then write to output file.

My code is parsing the xml messages but is not looping for 2 minutes or writing to the output file. Can anyone help with this please?

I can’t use crontab or gawk.So i need to change the strftime to something else but not sure.

```


awk 'BEGIN { INTERVAL=120;        NEXT=strftime("%s")+120; }

    {
        if(strftime("%s") >= NEXT)
        {
           printf( "\nSummary\n" );
           for( x in agcount )
              printf( "%s,%d\n", x, agcount[x] ) | "sort";

           # Clear out old values
           for( x in agcount)
                   delete agcount[x];

           NEXT=strftime("%s")+120;
        }

        gsub( ">", "" );        # strip uneeded junk and make "foo bar" easy to capture
        gsub( " ", "~" );
        gsub( "<", " " );

        for( i = 1; i <= NF; i++ )          # snarf up each name=value pair
        {
            if( split( $(i), a, "=" ) == 2 )
            {
                gsub(  "\"", "", a[2] );
                gsub(  "~", " ", a[2] );
                values[a[1]] = a[2];
            }
        }

        #gcount[values["Gender"]]++;         # collect counts
        #acount[values["Age"]]++;
        agcount[values["Gender"]","values["Age"]]++;

        printf( "%s %s %s %s\n", values["NAME"], values["Age"], values["D.O.B"], values["Gender"] );
    }' input-file


```Thank you all

James

---

### Post by JamesOwen on 2012-02-07
Hay guy's,

Can anyone help with this problem please.

Thanks

---

