---
title: "AWK Script to subtract hours from a date-time field"
date: 2009-04-06
forum: Programming Talk
---

### Post by Lex Luthor on 2009-04-06
Hello,

   I need some help here.
   I have a service that logs several lines about some events to syslog and I made a script to send those entries to a postgresql DB.

   In the DB, I have the following coluns:
    data_inic (date)
    time_inic (time without TZ)
    data_final (date)
    time_final (time without TZ)
    retension  (string)

   In syslog, the line logged contains ONLY data_final, time_final and retension, so I have to calculate data_inic and time_inic before I insert into BD. The retension time is given in hours,minutes and seconds, like: 152:45:30.

    So, my sh script basically gets syslog lines, and call an AWK script that gets each field, calculates the data_inic/time_inic and then send it to BD.

    The problem I am having is that the calculations are strange, data_inic and time_inic are being inserted wrong. I suppose it's a timezone related to mktime or strftime... I don't know... somebody could help me, please ?

   This is what I did:
[LIST=1]
[*]got the date of "zero day" to variable dia0 (1970-01-01)
[*]divide retension hours by 24 to know how many days I should add to dia0
[*]generate a timestamp for this modyfied dia0 (mktime)
[*]generate a timestamp for data_final (mktime), gotten from syslog
[*]subtract both timestamps
[*]generate data_inic with strftime (data_final is only the rest of the hours from step 2
[/LIST]

   ```

      dia0="1970-01-01"
      split(dia0, dia0_split, "-")
.
.
.
 # Agora fazemos o calculo para achar a hora de atribuicao do IP
  split(retencao, retencao_split, ":")
  horas_retencao = retencao_split[1]
  dias = int(horas_retencao / 24);
  resto_horas_retencao = horas_retencao % 24;
  dia0_dia = dias+1;
  retencao_timestamp = mktime(dia0_split[1]" "dia0_split[2]" "dia0_dia" "resto_horas_retencao" "retencao_split[2]" "retencao_split[3]" 0")

  split(data_final, data_f_split, "-")
  split(hora_final, hora_f_split, ":")
  hora_termino_timestamp = mktime (data_f_split[1]" "data_f_split[2]" "data_f_split[3]" "hora_f_split[1]" "hora_f_split[2]" "hora_f_split[3]" 0")
  hora_inicio_timestamp = hora_termino_timestamp - retencao_timestamp

  hora_inicio_str=strftime("%F %T", hora_inicio_timestamp)
  split(hora_inicio_str, data_split, " ")
  data_inicio = data_split[1]
  hora_inicio = data_split[2]


```


Thanks anybody for any help.....

---

### Post by Arndt on 2009-04-06
> **Lex Luthor said:**
> Hello,

   I need some help here.
   I have a service that logs several lines about some events to syslog and I made a script to send those entries to a postgresql DB.

   In the DB, I have the following coluns:
    data_inic (date)
    time_inic (time without TZ)
    data_final (date)
    time_final (time without TZ)
    retension  (string)

   In syslog, the line logged contains ONLY data_final, time_final and retension, so I have to calculate data_inic and time_inic before I insert into BD. The retension time is given in hours,minutes and seconds, like: 152:45:30.

    So, my sh script basically gets syslog lines, and call an AWK script that gets each field, calculates the data_inic/time_inic and then send it to BD.

    The problem I am having is that the calculations are strange, data_inic and time_inic are being inserted wrong. I suppose it's a timezone related to mktime or strftime... I don't know... somebody could help me, please ?

   This is what I did:
[LIST=1]
[*]got the date of "zero day" to variable dia0 (1970-01-01)
[*]divide retension hours by 24 to know how many days I should add to dia0
[*]generate a timestamp for this modyfied dia0 (mktime)
[*]generate a timestamp for data_final (mktime), gotten from syslog
[*]subtract both timestamps
[*]generate data_inic with strftime (data_final is only the rest of the hours from step 2
[/LIST]

   ```

      dia0="1970-01-01"
      split(dia0, dia0_split, "-")
.
.
.
 # Agora fazemos o calculo para achar a hora de atribuicao do IP
  split(retencao, retencao_split, ":")
  horas_retencao = retencao_split[1]
  dias = int(horas_retencao / 24);
  resto_horas_retencao = horas_retencao % 24;
  dia0_dia = dias+1;
  retencao_timestamp = mktime(dia0_split[1]" "dia0_split[2]" "dia0_dia" "resto_horas_retencao" "retencao_split[2]" "retencao_split[3]" 0")

  split(data_final, data_f_split, "-")
  split(hora_final, hora_f_split, ":")
  hora_termino_timestamp = mktime (data_f_split[1]" "data_f_split[2]" "data_f_split[3]" "hora_f_split[1]" "hora_f_split[2]" "hora_f_split[3]" 0")
  hora_inicio_timestamp = hora_termino_timestamp - retencao_timestamp

  hora_inicio_str=strftime("%F %T", hora_inicio_timestamp)
  split(hora_inicio_str, data_split, " ")
  data_inicio = data_split[1]
  hora_inicio = data_split[2]


```


Thanks anybody for any help.....

Try inserting debug printouts at interesting points in the script. For example, what are the values of hora_inicio_timestamp, hora_inicio_str and data_inicio and hora_inicio?

It might be a locale problem (different date conventions in Spanish and Engllish), but I can't say for sure yet.

---

### Post by Lex Luthor on 2009-04-06
I've done that, but I midified a little the script so that it would be more simple, and noticed something interesting.

This is the new script:

     ```

  split(retencao, retencao_split, ":")

  # Transform hours and minutes from retension (in the form HH:MM:SS) in seconds (the HH from retension may be over 60 hours):
  horas_sec_ret = retencao_split[1] * 60 * 60;
  min_sec_ret   = retencao_split[2] * 60;
  total_sec_ret = horas_sec_ret + min_sec_ret + retencao_split[3];

  print "Total sec: "total_sec_ret;

  hora_termino_timestamp = mktime (data_f_split[1]" "data_f_split[2]" "data_f_split[3]" "hora_f_split[1]" "hora_f_split[2]" "hora_f_split[3]" 0")
  print "DataF : "data_f_split[1]" "data_f_split[2]" "data_f_split[3]" "hora_f_split[1]" "hora_f_split[2]" "hora_f_split[3] ;
  print "End Timestamp : "hora_termino_timestamp;
  hora_inicio_timestamp = hora_termino_timestamp - total_sec_ret;


```

The debug shows something interesting:
    For the inic date: 2006-11-21 08:52:48
    Retension        : 1:01:59
    I got: 
      ```
Total sec: 3719
            End Timestamp : 1164109968
 
```

  But If I type on the prompt: 
       ```
 awk '{print mktime("2009 11 21 08 52 48");}'
```
  the timestamp returned is: **1258800768**


   And if I put on the BEGIN statement:
       **TZ=UTC**

   I get : ```
End Timestamp : 1164117070
```

   But after *strftime("%F %T", hora_inicio_timestamp)* it still is transformed to :
```
2006-11-21 08:50:49
```

   But if I set TZ=UTC on the Prompt, I get the RIGHT value:
   ```
2006-11-21 07:50:49
```

---

