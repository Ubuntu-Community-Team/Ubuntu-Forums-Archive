---
title: "[Python] Help Finish my Weather Indicator"
date: 2011-05-19
forum: Programming Talk
---

### Post by juancarlospaco on 2011-05-19
Help me finish my Weather Indicator, and i will make an English version.

Its Python, GPL, Lightweight, 
and comes with additional information that others dont have (Thermal, Dew Point, ...).

[B]The missing part is a Loop to refresh the info if Internet connection is available,
as well any improvement are welcome too, as i said its not finished.[/B]

It uses PywAPI (needs to be on the same folder): [http://code.google.com/p/python-weather-api/downloads/detail?name=pywapi-0.2.2.tar.gz&can=2&q=](http://code.google.com/p/python-weather-api/downloads/detail?name=pywapi-0.2.2.tar.gz&can=2&q=)
Or sudo apt-get install python-pywapi

```

#!/usr/bin/env python
# -*- coding: utf-8 -*-
#
################################################################################
# MicroClima : LightWeight Weather Indicator.
################################################################################
#
# Uncomment this lines to Speed Up the program
#try:
#    import psyco  # Speed Up if avaliable
#    psyco.full()
#except ImportError:
#    print(" ")
#    print(" No PYTHON-PSYCO avaliable, this application will run slower... ")
#    print(" ")
#    pass
# End of Speed Up

# imports
import gobject
import gtk
import appindicator
import pywapi
import commands
import os
from datetime import datetime

def quit(widget, data=None):
    gtk.main_quit() # QQ

# Main codez
if __name__ == "__main__":

    # Auto-Detect Current System language
    #local = commands.getoutput("locale | grep LANGUAGE | cut -c16,17")

    # Read or create the config file
    if os.path.exists(os.path.join(os.getenv("HOME"),".microclima/"))==False:
        os.mkdir(os.path.join(os.getenv("HOME"),".microclima/"))
        os.system('echo "Buenos Aires, AR" > $HOME/.microclima/microclima.config')
    try:
        place = commands.getoutput("cat $HOME/.microclima/microclima.config")
        print place
    except:
        os.system('echo "Buenos Aires, AR" > $HOME/.microclima/microclima.config')
        print ('Default config created, please edit $HOME/.microclima/microclima.config')
        place = commands.getoutput("cat $HOME/.microclima/microclima.config")

    # Obtiene la Info climatica inicialmente
    #google_result = pywapi.get_weather_from_google(place, hl = local)
    #google_result = pywapi.get_weather_from_google(place, hl = 'en') # English
    google_result = pywapi.get_weather_from_google(place, hl = 'es') # Español

    # Creo el indicador
    ind = appindicator.Indicator ("MicroClima", "indicator-messages", \
    appindicator.CATEGORY_APPLICATION_STATUS)
    ind.set_status (appindicator.STATUS_ACTIVE)
    ind.set_attention_icon ("indicator-messages-new")

    # Icono para el indicador
    #Tnow = google_result['current_conditions']['temp_f'] + "ºF" #Farenheit icon
    Tnow = google_result['current_conditions']['temp_c'] + "ºC"
    ind.set_label(Tnow)
    ind.set_icon("JuanCarlosPaco") # write a non-sense == no icon

    def cambia(valor,a):
        valor = float(valor)
        if a=='C':
            return str(valor - 32 * 9/5)
        elif a == 'K':
            return str(valor + 273)
        elif a == 'F':
            return str(valor * 9/5 + 32)

    # creo un menu
    menu = gtk.Menu()

    # Lista de Items
    #item0 = "" # Reserved for Future use
    #
    kamb = cambia(google_result['current_conditions']['temp_c'], 'K') # Kelvin
    kt = str(kamb) # Paso el Integer a String
    hora = datetime.time(datetime.now()).hour # la hora ahora
    if hora < 7 or hora > 19:
        nightday = "Noche " # es de noche
        icn = "&#9681;"
    else:
         nightday = "Dia " # es de dia
         icn = "&#9788;"
    item1 = str(icn + " Temp: " + google_result['current_conditions']['temp_c']\
     + "º Celsius, " + google_result['current_conditions']['temp_f'] + \
     "º Farenheit, " + kt + "º Kelvin") # Temp now
    #
    item2 = str(nightday + google_result['current_conditions']['condition'] + \
    " en " +google_result['forecast_information']['city']) # Place
    #
    # Calculo de Aproximacion la Sensacion Termica
    # ver: http://www.lenntech.es/calculadoras/viento/sensacion-termica.htm
    # T° aparente = 33 + (T aire- 33)*(0.474 + 0.454&#8730;(v)-0.0454.v)
    strv = google_result['current_conditions']['wind_condition'] # es un string
    pv = [float(s) for s in strv.split() if s.isdigit()] # le afano lo numeros
    v = float(pv[0]) # es un flotante
    #print v # imprime el flotante
    #
    # Este algorritmo saca la sensacion termica, recordar que v debe ser Float()
    ster = int(33 + ( int(google_result['current_conditions']['temp_c'])- 33)*\
    (0.474 + 0.454 * ((v)**(1/2))-0.0454*v) + 1)
    #
    stc = str(ster)
    #print ster
    stf = cambia(ster, 'F')
    item3 = str("Termica: " + stc + "º Celsius, Thermal: " + stf + "º Farenheit")
    #
    if v < 1:
        beauf = "Calma"
    elif v < 5:
        beauf = "Ventolina"
    elif v < 11:
        beauf = "Brisa muy debil"
    elif v < 19:
        beauf = "Brisa debil"
    elif v < 19:
        beauf = "Brisa Moderada"
    elif v < 28:
        beauf = "Brisa fresca"
    elif v < 49:
        beauf = "Brisa fuerte"
    elif v < 61:
        beauf = "Viento Moderado"
    elif v < 74:
        beauf = "Viento fuerte"
    elif v < 88:
        beauf = "Viento muy fuerte"
    elif v < 102:
        beauf = "Vientos Huracanados"
    elif v > 103:
        beauf = "Tornado!"
    else:
        beauf = "?"
    item4 = str(google_result['current_conditions']['wind_condition'] + ", Escala Beaufort: " + beauf )
    #
    #  punto de rocio
    hp = google_result['current_conditions']['humidity'] # es un string
    hv = [str(a) for a in hp if a.isdigit()] # le afano lo numeros
    h = int(str(hv[0]) + str(hv[1])) # es un integer
    #print h
    pr = ((h / 100.0) ** (1/8)) * (110 + int(google_result['current_conditions']['temp_c']) ) - 110
    rocio = str(pr)
    item9 = str(google_result['current_conditions']['humidity'] + ", Punto de Rocio: " + rocio + "º Celsius.") # Humidity
    #
    if v < 1:
        mar = "Calma"
    elif v < 5:
        mar = "Olas chicas, sin espuma"
    elif v < 11:
        mar = "Crestas de ola, sin romper"
    elif v < 19:
        mar = "Olas chicas, crestas rompientes."
    elif v < 19:
        mar = "Olas medianas, crestas rompientes."
    elif v < 28:
        mar = "Olas grandes, crestas rompientes."
    elif v < 49:
        mar = "Olas grandes rompientes, con poca espuma."
    elif v < 61:
        mar = "Olas grandes rompientes con mucha espuma."
    elif v < 74:
        mar = "Olas muy grandes rompientes con mucha espuma."
    elif v < 88:
        mar = "Olas gigantes rompientes con mucha espuma."
    elif v < 102:
        mar = "Olas gigantes rompientes, visibilidad reducida"
    elif v > 103:
        mar = "Olas enormes rompientes, visibilidad casi nula!"
    else:
        mar = "?"
    item10 =  str("Aspecto del mar: " + mar)# Beaufort Based
    #
    # Forecast
    if google_result['forecasts'][0]['day_of_week'] == "Sat":
        markSat = "&#10038;"
    elif google_result['forecasts'][0]['day_of_week'] == "Sun":
        markSat = "&#10038;"
    elif google_result['forecasts'][0]['day_of_week'] == "sáb":
        markSat = "&#10038;"
    elif google_result['forecasts'][0]['day_of_week'] == "dom":
        markSat = "&#10038;"
    else:
        markSat = " "
    item5 = str(markSat + google_result['forecasts'][0]['day_of_week']) + ": " + \
    google_result['forecasts'][0]['low'] + "ºC Min / " + \
    google_result['forecasts'][0]['high'] + "ºC Max (" + \
    google_result['forecasts'][0]['condition'] + ")" + markSat # Day
#
    if google_result['forecasts'][1]['day_of_week'] == "Sat":
        markSat = "&#10038;"
    elif google_result['forecasts'][1]['day_of_week'] == "Sun":
        markSat = "&#10038;"
    elif google_result['forecasts'][1]['day_of_week'] == "sáb":
        markSat = "&#10038;"
    elif google_result['forecasts'][1]['day_of_week'] == "dom":
        markSat = "&#10038;"
    else:
        markSat = " "
    item6 = str(markSat + google_result['forecasts'][1]['day_of_week']) + ": " + \
    google_result['forecasts'][1]['low'] + "ºC Min / " + \
    google_result['forecasts'][1]['high'] + "ºC Max (" + \
    google_result['forecasts'][1]['condition'] + ")" + markSat  # Day
#
    if google_result['forecasts'][2]['day_of_week'] == "Sat":
        markSat = "&#10038;"
    elif google_result['forecasts'][2]['day_of_week'] == "Sun":
        markSat = "&#10038;"
    elif google_result['forecasts'][2]['day_of_week'] == "sáb":
        markSat = "&#10038;"
    elif google_result['forecasts'][2]['day_of_week'] == "dom":
        markSat = "&#10038;"
    else:
        markSat = " "
    item7 = str(markSat + google_result['forecasts'][2]['day_of_week']) + ": " + \
    google_result['forecasts'][2]['low'] + "ºC Min / " + \
    google_result['forecasts'][2]['high'] + "ºC Max (" + \
    google_result['forecasts'][2]['condition'] + ")" + markSat  # Day
#
    if google_result['forecasts'][3]['day_of_week'] == "Sat":
        markSat = "&#10038;"
    elif google_result['forecasts'][3]['day_of_week'] == "Sun":
        markSat = "&#10038;"
    elif google_result['forecasts'][3]['day_of_week'] == "sáb":
        markSat = "&#10038;"
    elif google_result['forecasts'][3]['day_of_week'] == "dom":
        markSat = "&#10038;"
    else:
        markSat = " "
    item8 = str(markSat + google_result['forecasts'][3]['day_of_week']) + ": " + \
    google_result['forecasts'][3]['low'] + "ºC Min / " + \
    google_result['forecasts'][3]['high'] + "ºC Max (" + \
    google_result['forecasts'][3]['condition'] + ") " + markSat  # Day

    # creo elemento 0 de menu
    #menu_item1 = gtk.MenuItem(item1)
    #menu.append(menu_item1)
    #menu_item1.show()

    # creo elemento 1 de menu
    menu_item1 = gtk.MenuItem(item1)
    menu.append(menu_item1)
    menu_item1.show()

    # creo elemento 2 de menu
    menu_item2 = gtk.MenuItem(item2)
    menu.append(menu_item2)
    menu_item2.show()

    # creo elemento 3 de menu
    menu_item3 = gtk.MenuItem(item3)
    menu.append(menu_item3)
    menu_item3.show()

    # creo elemento 4 de menu
    menu_item4 = gtk.MenuItem(item4)
    menu.append(menu_item4)
    menu_item4.show()

    # creo elemento 9 de menu
    menu_item9 = gtk.MenuItem(item9)
    menu.append(menu_item9)
    menu_item9.show()

     # creo elemento 9 de menu
    menu_item10 = gtk.MenuItem(item10)
    menu.append(menu_item10)
    menu_item10.show()

    # Soy un Separador y vengo a Separar
    separator = gtk.SeparatorMenuItem()
    menu.append(separator)
    separator.show()

    # creo elemento 5 de menu
    menu_item5 = gtk.MenuItem(item5)
    menu.append(menu_item5)
    menu_item5.show()

    # creo elemento 6 de menu
    menu_item6 = gtk.MenuItem(item6)
    menu.append(menu_item6)
    menu_item6.show()

    # creo elemento 7 de menu
    menu_item7 = gtk.MenuItem(item7)
    menu.append(menu_item7)
    menu_item7.show()

    # creo elemento 8 de menu
    menu_item8 = gtk.MenuItem(item8)
    menu.append(menu_item8)
    menu_item8.show()

    separator = gtk.SeparatorMenuItem()
    menu.append(separator)
    separator.show()

    # This is the QQ
    image = gtk.ImageMenuItem(gtk.STOCK_QUIT)
    image.connect("activate", quit)
    menu.append(image) # Cuando este Terminado y Testeado, esconderlo de la GUI
    image.show();

    ind.set_menu(menu)
    gtk.main()

```

:)
Thanks !

---

### Post by juancarlospaco on 2011-05-20
**... Bump !**

---

### Post by Tony Flury on 2011-05-20
I think the problem is that people aren't really sure what you need/want/expect.

your code is not spectacular either - you have ignored most of the decent features of python - like functions, classes etc.

For a start - those long chains of if/elses - there has to be a better way of coding that - i would go with a list (storing the limit and text), and a tight loop which compares the value to the limit.

if you want to do a regular check for your internet connection - you need something like a timer that fires regularly - and tries to fetch the data.

---

### Post by simeon87 on 2011-05-20
You haven't gotten a response so far so consider it from our perspective: why would someone finish your weather indicator, if we could work on our own programming projects?

Why don't you just post the specific things you're having difficulty with and we can help you with that?

---

### Post by juancarlospaco on 2011-05-20
> **Tony Flury said:**
> the problem is that people aren't really sure what you need/want/expect.

> **juancarlospaco said:**
> 
**The missing part is a Loop to refresh the info if Internet connection is available**



> **Tony Flury said:**
> your code is not spectacular either - you have ignored most of the decent features of python - like functions, classes etc.

> **juancarlospaco said:**
> 
**as well any improvement are welcome too, as i said its not finished.**


> **Tony Flury said:**
> For a start - those long chains of if/elses - there has to be a better way of coding that - i would go with a list (storing the limit and text), 

I try, but it didnt work.

---

### Post by juancarlospaco on 2011-05-20
> **simeon87 said:**
> why would someone finish your weather indicator, if we could work on our own programming projects?

why would someone post on this forum, if we could work on our own forum?

> **simeon87 said:**
> Why don't you just post the specific things you're having difficulty with and we can help you with that?

I do that on the Past, and people reply : 
*Why don't you just post the code and we can help you with that?*  :(

---

### Post by cgroza on 2011-05-20
> **juancarlospaco said:**
> why would someone post on this forum, if we could work on our own forum?

I do that on the Past, and people reply : 
*Why don't you just post the code and we can help you with that?* 

You analogy does not apply, posting on a forum is not working on a forum. You could work on your own forum if that gives the solution to your problem.

You can't expect people to implement a whole feature for you. We help with specific clear problems, like design difficulties, ways to do things, how and with what.

---

### Post by juancarlospaco on 2011-05-20
I think that this is Programming Talk where people Talk about Programming, 
to help and share, just for the idea of *help and share* itself, because they can.

---

### Post by juancarlospaco on 2011-05-20
> **cgroza said:**
> You analogy does not apply

I dont say that my analogy apply.

> **cgroza said:**
> You can't expect people to implement a whole feature for you. 

ok, 1 loop is too much whole feature, thank you very much.

---

### Post by juancarlospaco on 2011-05-20
Thanks to all people participating here. 
 &#664;&#8255;&#664;

---

### Post by cgroza on 2011-05-20
> **juancarlospaco said:**
> I dont say that my analogy apply.



ok, 1 loop is too much whole feature, thank you very much.
You got the idea, a loop, put it in thread which has a timer and what you need in it.

---

### Post by juancarlospaco on 2011-05-20
> **cgroza said:**
> You got the idea, a loop, 

No.
Just someone tell me thats what i need to do.
I just copied the script into /etc/cron.hourly/ and keep looking for help somewhere.

---

### Post by Tony Flury on 2011-05-21
You have now 3 methods of implementing your internet check. why not actually try one ?

Also - when you said you tried a list and it did not work (as an alternative to your if/else chains),  do you have an example of the code you tried - i can assure you that the technique does work.

Although none of us has corrected your code, or finished your application, if you read what people has written - we are trying to help you by helping you learn and improve. You would not learn much if someone just handed you a re-written program.

---

### Post by simeon87 on 2011-05-21
> **juancarlospaco said:**
> I do that on the Past, and people reply : 
*Why don't you just post the code and we can help you with that?*  :(

Well, yes, because we need to see code to see what's going wrong. If someone posts that something is wrong with their code and that "it's showing the wrong numbers!!" then we really have to see the code.

> **juancarlospaco said:**
> ok, 1 loop is too much whole feature, thank you very much.

Then why ask others to implement it? Although the forum rules say that we don't do homework for students, the same reasoning applies here: if you want to learn how to do it, then try it yourself first and if it's still not working then ask for help.

---

### Post by juancarlospaco on 2011-05-21
> **Tony Flury said:**
> You have now 3 methods of implementing your internet check

i didnt know that

> **Tony Flury said:**
> Also - when you said you tried a list and it did not work (as an alternative to your if/else chains)

Yes

> **Tony Flury said:**
> do you have an example of the code you tried

No
I have to erase the lines to get my program back to work.

On the past i posted some code with lots of commented out non-working lines,
and people say thats too dirty and hard to read, so i try to erase all unnecessary lines :(

> **Tony Flury said:**
> i can assure you that the technique does work.

No

> **Tony Flury said:**
> You would not learn much if someone just handed you a re-written program.

Yes

---

### Post by juancarlospaco on 2011-05-21
> **simeon87 said:**
> "it's showing the wrong numbers!!" 

"it's not Updating the Info!!"

> **simeon87 said:**
> Then why ask others to implement it?

Because i can, because this is the place to share programming help i think.

> **simeon87 said:**
> Although the forum rules say that we don't do homework for students

I didnt say thats homework, im 27
still not working then im asking for help.

---

### Post by Tony Flury on 2011-05-21
I can assure you it took me 3 minutes to write a python list that works the way your if/else chain works.

And if you read through the replies you will see three different options for getting internet updates.
[LIST=1]
[*]A timer,
[*]A 2nd Thread with a loop
[*]A regular update that runs as a cron job
[/LIST]

any of those three would work - although some would be more complex.

Anyway - I have contributed all I can to this - good luck.

---

### Post by simeon87 on 2011-05-21
> **juancarlospaco said:**
> Because i can, because this is the place to share programming help i think.

Exactly, it's about helping others with programming, not doing programming work for others.

> **juancarlospaco said:**
> I didnt say thats homework, im 27
still not working then im asking for help.

I didn't say it was homework but it's the same attitude of a student who expects others to do it for him. People won't do work for you but we can help with your own efforts. If you try any of the mentioned approaches, such as timers or threads, and it doesn't work then we can help out with where it goes wrong.

---

### Post by juancarlospaco on 2011-05-21
/solved

Lots of words no one post an example of loop or checking internet or something.

---

