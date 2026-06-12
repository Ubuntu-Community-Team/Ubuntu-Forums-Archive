---
title: "Script question - Python"
date: 2014-12-22
forum: Programming Talk
---

### Post by DiogoSaraiva on 2014-12-22
Hi,

Why this its not working:

```

#!/usr/bin/python
# -*- coding: utf-8 -*-


import os
import time
#....more code.......
with open('log-fonte-alimentacao.txt', 'a') as file:
    file.write("\n\nFonte de Alimentação Desligada\n")
    file.write(os.system('date'))
#...more code......

```

What should do i do...
Thanks in advance...

Diogo

---

### Post by ofnuts on 2014-12-22
Because the returned value of "os.system('date')" is the return code of the "date" command, not the string the "date" command prints out.  If you want the string you should be using [os.popen() or the subprocess library]("http://stackoverflow.com/questions/3503879/assign-output-of-os-system-to-a-variable-and-prevent-it-from-being-displayed-on").

Byt it would be more efficient to use the functions in the [time library]("https://docs.python.org/2/library/time.html").

---

### Post by Vaphell on 2014-12-22
what exactly does not work? does it say anything?
Either way i'd suspect that file.write() expects a string, is os.system() actually returning one?

Also why do you use commandline *date* command if you can use python native *datetime* module, superior in this context?
[https://docs.python.org/2/library/datetime.html](https://docs.python.org/2/library/datetime.html)

---

### Post by DiogoSaraiva on 2014-12-22
returns me:
TypeError: expected a character buffer object


```

#!/usr/bin/python
# -*- coding: utf-8 -*-


import os
import time
import datetime


horas = datetime.datetime.now()


with open('date.txt', 'a') as file:
	file.write("\n\nFonte de Alimentação Desligada\n")
	file.write(horas)
file.close()



```

---

### Post by ofnuts on 2014-12-22
datetime.datetime.now() is a "datetime" object,  you have to convert it to a string, for instance using its strftime method: 
```
datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
```

---

### Post by DiogoSaraiva on 2014-12-22
Thanks to all. We made it...
Here is the final code: [https://github.com/DiogoSaraiva/Private/blob/master/fontealimentacao.py](https://github.com/DiogoSaraiva/Private/blob/master/fontealimentacao.py)
But the script consumes so much CPU... and the fans always in MAX when I run the script...
any idea??
for less CPU consuming??

Thanks again

---

### Post by ofnuts on 2014-12-22
If you think the script is looping without really executing the sleep() then look at the produced log... Since you write the time in it you can tell if you are actually logging things every 6 seconds or at a much shorter interval. Note that of none of your conditions (GPIO.input(X)) is true, you have a much shorter loop.

Otherwise you may want to ask in a forum dedicated to the Raspberry Pi.

PS: you should avoid all that code duplication...

---

### Post by DiogoSaraiva on 2014-12-22
not logging things every 6 seconds, i guess....
only when i switch ON or OFF my power supply (not of PC, is other power supply like lab power supply) and it send a signal telling that was powered ON or OFF...
only logs when "GPIO.input(7) == True" or "GPIO.input(8) == True" which is when i power ON or OFF my power supply...
And it's not a Raspberry Pi, now I have a mini PC (Giada A51B) that is more powerful than my old raspberry...
in code says virtGPIO, is a virtual GPIO is a arduino connected to the pc ([see here more info about virtGPIO]("https://github.com/BLavery/virtual-GPIO")).... not a Raspberry pi GPIO...

Thanks

---

### Post by ofnuts on 2014-12-23
At that point it shouldn't be a matter of guessing... If you add a logging instruction after the sleep(1), what do you get in the log?

What actual values are returned by the calls to GPIO (this should be made part of the log)?

---

### Post by DiogoSaraiva on 2014-12-23
in log I get 
"Fonte de Alimentação Desligada" and date  or "Fonte de Alimentação Ligada" and date ONLY each time I turn off or turn on my power supply

Translations:

Fonte de Alimentação Desligada = Power Supply Off 
Fonte de Alimentação Ligada = Power Supply On

---

### Post by Vaphell on 2014-12-23
being anal here, but like ofnuts said you should roll that almost identical code into a function, teeth hurt by looking at such a blatant copypasta ;-)

```
def log_msg( msg ):
    print( msg )
    with open('/home/diogosaraiva/Documentos/Projetos-Python/fontealimentacao-log.txt', 'a') as file:
        file.write("\n\n{}\n".format(msg) )
        file.write(datetime.datetime.now().strftime("%d-%m-%Y %H:%M:%S"))

while True:
    if GPIO.input(7):
        log_msg( "Fonte de Alimentação Ligada" )
        time.sleep(5)
    if GPIO.input(8):
        log_msg( "Fonte de Alimentação Desligada" )
        time.sleep(5)
    time.sleep(1)
```

---

### Post by DiogoSaraiva on 2014-12-23
[FONT=Menlo]  File "Vaphell.py", line 15[/FONT]
[FONT=Menlo]    with open('/home/diogosaraiva/Vaphell-log.txt', 'a') as file:[/FONT]
[FONT=Menlo]       ^[/FONT]
[FONT=Menlo]SyntaxError: invalid syntax[/FONT]

another error....

```

#!/usr/bin/python
# -*- coding: utf-8 -*-


import virtGPIO as GPIO
import datetime
import time


GPIO.setup(7, GPIO.IN)
GPIO.setup(8, GPIO.IN)


GPIO.cleanup


def log_msg(msg):
    print(datetime.datetime.now().strftime("%d-%m-%Y %H:%M:%S")
    with open('/home/diogosaraiva/Vaphell-log.txt', 'a') as file:
        file.write("\n\n{}\n".format(msg))
        file.write(datetime.datetime.now().strftime("%d-%m-%Y %H:%M:%S"))


while True:
    if GPIO.input(7):
        log_msg("Fonte de Alimentação Ligada")
        time.sleep(5)
    if GPIO.input(8):
        log_msg("Fonte de Alimentação Desligada")
        time.sleep(5)
    time.sleep(1)

```

---

### Post by Vaphell on 2014-12-23
missing closing paren in the print line

```
print[COLOR="#FF0000"]([/COLOR]datetime.datetime.now().strftime[COLOR="#0000CD"]([/COLOR]"%d-%m-%Y %H:%M:%S"[COLOR="#0000CD"])[/COLOR]
```

---

### Post by DiogoSaraiva on 2014-12-24
Not working at first with that modification, but I write manually again the script and then worked.... why? weird....
the exactly same script....
And consumes less CPU I Think, at least the fans are more quiet....
Thank you very much Vaphell and others that tried or helped me...

AND here is the almost final code:

```

[COLOR=#b22222][FONT=Menlo]**#!/usr/bin/python**[/FONT]
[FONT=Menlo]**# -*- coding: utf-8 -*-**[/FONT][/COLOR]
[FONT=Menlo]
[/FONT]
[FONT=Menlo][COLOR=#34bbc7]**import**[/COLOR] virtGPIO [COLOR=#34bbc7]**as**[/COLOR] GPIO[/FONT]
[FONT=Menlo][COLOR=#34bbc7]**import**[/COLOR] datetime[/FONT]
[COLOR=#34BBC7][FONT=Menlo]**import**[COLOR=#000000] time[/COLOR][/FONT][/COLOR]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]GPIO.setup(7, GPIO.IN)[/FONT]
[FONT=Menlo]GPIO.setup(8, GPIO.IN)[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]GPIO.cleanup[/FONT]
[FONT=Menlo]
[/FONT]
[COLOR=#5330E1][FONT=Menlo][COLOR=#34bbc7]**def**[/COLOR]** log_msg**[COLOR=#000000](msg):[/COLOR][/FONT][/COLOR]
[FONT=Menlo]        [COLOR=#34bbc7]**print**[/COLOR](datetime.datetime.now().strftime([COLOR=#34bd26]**"%d-%m-%Y %H:%M:%S"**[/COLOR]))[/FONT]
[COLOR=#34BD26][FONT=Menlo][COLOR=#34bbc7]**with**[/COLOR][COLOR=#000000] open([/COLOR]**'/home/diogosaraiva/Vaphell-log.txt'**[COLOR=#000000], [/COLOR]**'a'**[COLOR=#000000]) [/COLOR][COLOR=#34bbc7]**as**[/COLOR][COLOR=#000000] file:[/COLOR][/FONT][/COLOR]
[FONT=Menlo]                file.write([COLOR=#34bd26]**"\n\n{}\n"**[/COLOR].format(msg))[/FONT]
[FONT=Menlo]                file.write(datetime.datetime.now().strftime([COLOR=#34bd26]**"%d-%m-%Y %H:%M:%S"**[/COLOR]))[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo][COLOR=#34bbc7]**while**[/COLOR] True:[/FONT]
[FONT=Menlo]        [COLOR=#34bbc7]**if**[/COLOR] GPIO.input(7):[/FONT]
[COLOR=#34BD26][FONT=Menlo][COLOR=#000000]                log_msg([/COLOR]**"Fonte de Alimentação Ligada"**[COLOR=#000000])[/COLOR][/FONT][/COLOR]
[FONT=Menlo]                time.sleep(2)
[COLOR=#b22222]#               time.sleep(2) #maybe need this 2 seconds more time[/COLOR][/FONT]
[FONT=Menlo]        [COLOR=#34bbc7]**if**[/COLOR] GPIO.input(8):[/FONT]
[COLOR=#34BD26][FONT=Menlo][COLOR=#000000]                log_msg([/COLOR]**"Fonte de Alimentação Desligada"**[COLOR=#000000])[/COLOR][/FONT][/COLOR]
[FONT=Menlo]                time.sleep(2)
[COLOR=#b22222]#               time.sleep(2) #maybe need this 2 seconds more time[/COLOR][/FONT]
[FONT=Menlo]        time.sleep(1)[/FONT]

```



Thank you for all and happy Holidays...

---

### Post by ofnuts on 2014-12-24
That's why I am telling you to add another logging outside of these two tests. And what is important is the time at which these are logged (which will tell you if the sleep() did what you thought).

---

### Post by DiogoSaraiva on 2014-12-26
the time.sleep(2) is because my power supply sends a signal (because I put it a circuit with a NE555 and a PNP transistor and other components...) and its signal if I can vary between 1.5 and 3 seconds and if i not put time.sleep(2) next to "if GPIO.input(7):" when is true (when has a signal from my power supply) logs every microsecond or +/-...
like this:

```

Fonte de Alimentação Ligada
26-12-2014 08:29:30

Fonte de Alimentação Ligada
26-12-2014 08:29:30

Fonte de Alimentação Ligada
26-12-2014 08:29:30

Fonte de Alimentação Ligada
26-12-2014 08:29:30

Fonte de Alimentação Ligada
26-12-2014 08:29:30

Fonte de Alimentação Ligada
26-12-2014 08:29:30

Fonte de Alimentação Ligada
26-12-2014 08:29:30

Fonte de Alimentação Ligada
26-12-2014 08:29:30

Fonte de Alimentação Ligada
26-12-2014 08:29:30

Fonte de Alimentação Ligada
26-12-2014 08:29:30

Fonte de Alimentação Ligada
26-12-2014 08:29:30

Fonte de Alimentação Ligada
26-12-2014 08:29:31

Fonte de Alimentação Ligada
26-12-2014 08:29:31

Fonte de Alimentação Ligada
26-12-2014 08:29:31

Fonte de Alimentação Ligada
26-12-2014 08:29:31

Fonte de Alimentação Ligada
26-12-2014 08:29:31

Fonte de Alimentação Ligada
26-12-2014 08:29:31

Fonte de Alimentação Ligada
26-12-2014 08:29:31

Fonte de Alimentação Ligada
26-12-2014 08:29:31

Fonte de Alimentação Ligada
26-12-2014 08:29:31

Fonte de Alimentação Ligada
26-12-2014 08:29:32

Fonte de Alimentação Ligada
26-12-2014 08:29:32

Fonte de Alimentação Ligada
26-12-2014 08:29:32

Fonte de Alimentação Ligada
26-12-2014 08:29:32

Fonte de Alimentação Ligada
26-12-2014 08:29:32

Fonte de Alimentação Ligada
26-12-2014 08:29:32

Fonte de Alimentação Ligada
26-12-2014 08:29:32

Fonte de Alimentação Ligada
26-12-2014 08:29:32

Fonte de Alimentação Ligada
26-12-2014 08:29:32


```

Translation:

Fonte de Alimentação: Power Supply
Ligada: ON / [SIZE=1]connected[/SIZE]

Thanks

---

### Post by ofnuts on 2014-12-26
The logs above are showing that your code is looping badly and not really taking in account the sleep(), since you log about 10 times per second instead of once every 3 seconds or so... Better make a quick test on the side to see how long time.sleep(2) is really sleeping. Normally the parameter is a number of seconds, and on my Ubuntu this really sleeps 2 seconds but I have doubts about the implementation you are using or something is interrupting your program every 100ms and making it exit the sleep() routine early.

Note: logs are a lot easier to read/post-process when each event if logged in one line with the time at the beginning (in an easily sorted format):

```

2014-01-31 01:02:03: Fonte de Alimentação Ligada

```

---

### Post by DiogoSaraiva on 2014-12-26
[COLOR=#000000][I]" since you log about 10 times per second instead of once every 3 seconds or so" 
[/I]
it's only an example how its log without the time.sleep(2) and only logs when I turn on or turn off my power supply... ok?
i don't turn on and off every 3 seconds...
but the signal to Virtual GPIO (Arduino) its about between 1.5 seconds and 2 seconds or maybe more...
since virtual gpio when detecting is always logging everytime during the between the 1.5 and 2 seconds.... do you understand?

the time.sleep(2) is for making counting only one time, each time I turn ON or OFF my power supply...

Understand?


If you understanded I will mark this post as SOLVED, because is solved, ok?

Cheers
[/COLOR]

---

