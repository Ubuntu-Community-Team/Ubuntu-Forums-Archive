---
title: "dbus glib problem (memory leak)"
date: 2009-01-30
forum: Programming Talk
---

### Post by MeduZa on 2009-01-30
Hello, I'm new programing with Dbus and Glib, I made a plug in for a 
project that I'm working on, to read the battery levels and state, this 
is my first time using this libraries.
The program works perfectly except that when it runs, it starts eating 
memory (something like 16Kb each time the FOR executes) on the 
dbus_g_proxy_call command.

every dbus_g_proxy_call eat ~4Kb.

I checked to see if maybe I forgot to free something or maybe I 
implemented the command in the wrong way but I can't find the memory leak.

Here is the code (and my first use of dbus):

```
//   battery.cpp
//  Thu Jan 15 18:47:27 2009
//  Copyright  2009  MeduZa
// <meduzapat at netscape.net>

//battery libraries
#include <iostream>
#include <sstream>
#include <vector>
#include <dbus/dbus-glib.h>
#include "system.hpp"

#define TOTAL_ITEMS 5      //total Items

/*********************************
  *       Variables Globales      *
  *********************************/
bool loaded = false;        //flag plugin loaded
int totalbaterias;        //batteries count

struct bateria{
     string udi;        //udi
     string nombre;        //info.product
     string tipo;        //battery.type
     string tecnologia;    //battery.technology not allwais available
     int carga;        //last_full-current
     string estado;        //if present , is chargable > is chargin / 
dischargin , N/A
};

vector<bateria> Tabla_Baterias;

/*********************************
  *        Funciones Ayuda        *
  *********************************/

int leeindice(string &udi){
     if(loaded){
         int conta;
         for(conta = 0;conta < totalbaterias ; conta ++)    if(udi == 
Tabla_Baterias[conta].udi) break;
         if(conta < totalbaterias) return conta;
     }
     return -1;
}

static DBusGProxy * get_dbus_proxy(const string &destino,const string 
&objpath,const string &iface){
     g_return_val_if_fail (destino.c_str() && objpath.c_str() && 
iface.c_str(), NULL);
     DBusGConnection *connection;
     DBusGProxy *proxy = NULL;
     GError *el_error = NULL;
     connection = dbus_g_bus_get(DBUS_BUS_SYSTEM, &el_error );
     if(connection != NULL){
         proxy = dbus_g_proxy_new_for_name(connection,destino.c_str(), 
objpath.c_str(), iface.c_str());
     }else g_warning("Failed to open connection to bus: %s",(el_error && 
el_error ->message) ? el_error ->message : "(unknown error)");
     if (el_error  != NULL) g_error_free(el_error );
     if (connection != NULL) dbus_g_connection_unref(connection);
     return proxy;
}

static gboolean error_happened(gboolean code, GError *es_error){
     g_return_val_if_fail(code || es_error != NULL, true);
     gboolean retval = false;
     if(!code){
         #ifdef DEBUG
             if(es_error->domain == DBUS_GERROR && es_error->code == 
DBUS_GERROR_REMOTE_EXCEPTION)
                 g_warning("Caught remote method exception %s: %s", 
dbus_g_error_get_name (es_error),es_error->message);
             else{
                 g_warning("Error: (%d) %s",
                 es_error->code, es_error->message);
             }
         #endif
         retval = true;
     }
     if(es_error != NULL) g_error_free(es_error);
     return retval;
}

bool leetodo(bateria &Bateria,gboolean lnombres,gboolean 
lcharge,gboolean lestado){
     GError *el_error = NULL;
     gboolean result;
     DBusGProxy *proxy = NULL;
     proxy = get_dbus_proxy("org.freedesktop.Hal", Bateria.udi.c_str(), 
"org.freedesktop.Hal.Device");
     if(lnombres){
         char *nombre, *tipo, *tecnologia;    //strings pointers for 
text data << need free
         result = dbus_g_proxy_call(proxy, "GetProperty", &el_error, 
G_TYPE_STRING, "info.product", G_TYPE_INVALID, G_TYPE_STRING, &nombre, 
G_TYPE_INVALID);
         if(error_happened(result, el_error)) Bateria.nombre = "N/A";
         else{
             Bateria.nombre = nombre;
             g_free(nombre);
         }
         el_error = NULL;
         result = dbus_g_proxy_call(proxy, "GetPropertyString", 
&el_error, G_TYPE_STRING, "battery.type",G_TYPE_INVALID, G_TYPE_STRING, 
&tipo, G_TYPE_INVALID);
         if(error_happened(result, el_error)) Bateria.tipo = "N/A";
         else{
             Bateria.tipo = tipo;
             g_free(tipo);
         }
         el_error = NULL;
         result = dbus_g_proxy_call(proxy, "GetProperty", &el_error, 
G_TYPE_STRING, "battery.reporting.technology", G_TYPE_INVALID, 
G_TYPE_STRING, &tecnologia, G_TYPE_INVALID);
         if(error_happened(result, el_error)) Bateria.tecnologia = "N/A";
         else{
             Bateria.tecnologia = tecnologia;
             g_free(tecnologia);
         }
     }
     if(lcharge){
         gint ultima, ahora;
         Bateria.carga  = 0;
         el_error = NULL;
         result = dbus_g_proxy_call(proxy, "GetProperty", &el_error, 
G_TYPE_STRING, "battery.charge_level.last_full", G_TYPE_INVALID, 
G_TYPE_INT, &ultima, G_TYPE_INVALID);
         if(!error_happened(result, el_error)){
             el_error = NULL;
             result = dbus_g_proxy_call(proxy, "GetProperty", &el_error, 
G_TYPE_STRING, "battery.charge_level.current",G_TYPE_INVALID, 
G_TYPE_INT, &ahora, G_TYPE_INVALID);
             if(!error_happened(result, el_error)){
                 if(ultima < 1) ultima = 1;
                 Bateria.carga = (ahora*100 / ultima*100) /100;
             }
         }
     }
     if(lestado){
         gboolean presente, recargable, cargando, descargando;
         el_error = NULL;
         result = dbus_g_proxy_call(proxy, "GetProperty", &el_error, 
G_TYPE_STRING, "battery.present",G_TYPE_INVALID, G_TYPE_BOOLEAN, 
&presente,G_TYPE_INVALID);
         if(!error_happened(result, el_error)){
             if(!presente) Bateria.estado  = "Missing";
             else{
                 el_error = NULL;
                 result = dbus_g_proxy_call(proxy, "GetProperty", 
&el_error, G_TYPE_STRING, "battery.is_rechargeable",G_TYPE_INVALID, 
G_TYPE_BOOLEAN, &recargable,G_TYPE_INVALID);
                 if(!error_happened(result, el_error)){
                     if(!recargable)    Bateria.estado  = "Ready";
                     else{
                         el_error = NULL;
                         result = dbus_g_proxy_call(proxy, 
"GetProperty", &el_error, G_TYPE_STRING, 
"battery.rechargeable.is_charging",G_TYPE_INVALID, G_TYPE_BOOLEAN, 
&cargando,G_TYPE_INVALID);
                         if(!error_happened(result, el_error)){
                             if(cargando) Bateria.estado  = "Charging";
                             else{
                                 el_error = NULL;
                                 result = dbus_g_proxy_call(proxy, 
"GetProperty", &el_error, G_TYPE_STRING, 
"battery.rechargeable.is_discharging",G_TYPE_INVALID, G_TYPE_BOOLEAN, 
&descargando, G_TYPE_INVALID);
                                 if(!error_happened(result, el_error)){
                                     if(descargando) Bateria.estado  = 
"Working";
                                     else Bateria.estado  = "Ready";
                                 }
                             }
                         }
                     }
                 }
             }
         }
     }
     if (proxy != NULL) g_object_unref(proxy);
     return true;
}

/*********************************
  *      Funciones Externas       *
  *********************************/

int Init(){        //returns total Items and try to init the plugin 
return -1 on fail
     if(!loaded){
         char **name_list;                //udi list names
         char **name_list_ptr;                //poiner for list names
         bateria Bateria_temp;                //temp bateria
         DBusGProxy *proxy;                //proxy handler
         GError *el_error = NULL;            //error handler
         gboolean resultado;                //result
         g_type_init ();                    //init g
         #ifdef DEBUG
             cout << "Internal plugin Data Initiation..." << endl;
         #endif
         //variables that need 2be started
         proxy = get_dbus_proxy("org.freedesktop.Hal", 
"/org/freedesktop/Hal/Manager", "org.freedesktop.Hal.Manager");
         if(proxy == NULL) return -1;
         #ifdef DEBUG
             cout << "Connection to the bus success" << endl;
         #endif
         resultado = dbus_g_proxy_call(proxy, "FindDeviceByCapability", 
&el_error, G_TYPE_STRING, "battery", G_TYPE_INVALID, G_TYPE_STRV, 
&name_list, G_TYPE_INVALID);
         if(error_happened(resultado, el_error))    return -1;
         #ifdef DEBUG
             cout << "Proxy success, getting data..." << endl;
         #endif
         g_object_unref(proxy);
         for (name_list_ptr = name_list,totalbaterias = 0; 
*name_list_ptr; name_list_ptr++,totalbaterias ++){
             #ifdef DEBUG
                 cout << "Getting Battery " << totalbaterias << " Data" 
<< endl;
             #endif
             Bateria_temp.udi = *name_list_ptr;
             leetodo(Bateria_temp,true,true,true);
             Tabla_Baterias.push_back(Bateria_temp);
         }
         g_strfreev (name_list);
         loaded = true;
         return TOTAL_ITEMS;
     }
}

string Get_Value(int index,string& udi){
     int indice = leeindice(udi);
     switch (index){
         case 0:return "N/A";
         break;                    //error return
         case 1:{                //funcion 1 Battery Name
             leetodo(Tabla_Baterias[indice],true,false,false);
             return Tabla_Baterias[indice].nombre;
         }break;
         case 2:{                //funcion 1 Battery type
             leetodo(Tabla_Baterias[indice],true,false,false);
             return Tabla_Baterias[indice].tipo;
         }break;
         case 3:{                //funcion 1 Battery technology
             leetodo(Tabla_Baterias[indice],true,false,false);
             return Tabla_Baterias[indice].tecnologia;
         }break;
         case 4:{                //funcion 1 Battery charge
             ostringstream converter;
             leetodo(Tabla_Baterias[indice],false,true,false);
             converter << Tabla_Baterias[indice].carga;
             return converter.str();
         }break;
         case 5:{                //funcion 1 Battery state
             leetodo(Tabla_Baterias[indice],false,false,true);
             return Tabla_Baterias[indice].estado;
         }break;
     }
}

void Destruct(){
     //TODO
     loaded = false;
}
```

I really inspect and rewrite the code but the memory leak still there :(

I need some help please.

---

### Post by Branimir on 2009-01-30
There are no obvious leaks but excuse me
Im stupid a little bit
I cannot figure out what this function does?

```

string Get_Value(int index,string& udi){
     int indice = leeindice(udi);
     switch (index){
         case 0:return "N/A";
         break;                    //error return
         case 1:{                //funcion 1 Battery Name
             leetodo(Tabla_Baterias[indice],true,false,false);
             return Tabla_Baterias[indice].nombre;
         }break;
         case 2:{                //funcion 1 Battery type
             leetodo(Tabla_Baterias[indice],true,false,false);
             return Tabla_Baterias[indice].tipo;
         }break;
         case 3:{                //funcion 1 Battery technology
             leetodo(Tabla_Baterias[indice],true,false,false);
             return Tabla_Baterias[indice].tecnologia;
         }break;
         case 4:{                //funcion 1 Battery charge
             ostringstream converter;
             leetodo(Tabla_Baterias[indice],false,true,false);
             converter << Tabla_Baterias[indice].carga;
             return converter.str();
         }break;
         case 5:{                //funcion 1 Battery state
             leetodo(Tabla_Baterias[indice],false,false,true);
             return Tabla_Baterias[indice].estado;
         }break;
     }
}

```

Greetsa, Branimir

---

### Post by nvteighen on 2009-01-30
Just a note. Have you used valgrind to detect the memory leak? (look for valgrind in the repos).

Use:
```

valgrind ./myprog

```

And post the output. You'll probably see a lot of "leaks" coming from GTK+ and related libraries, but don't worry.

---

### Post by bruce89 on 2009-01-30
Incidentally, you shouldn't have curly brackets in a case part of a switch statement.

---

### Post by MeduZa on 2009-01-30
> **Branimir said:**
> There are no obvious leaks but excuse me
Im stupid a little bit
I cannot figure out what this function does?

```

string Get_Value(int index,string& udi){
     int indice = leeindice(udi);
     switch (index){
         case 0:return "N/A";
         break;                    //error return
         case 1:{                //funcion 1 Battery Name
             leetodo(Tabla_Baterias[indice],true,false,false);
             return Tabla_Baterias[indice].nombre;
         }break;
         case 2:{                //funcion 1 Battery type
             leetodo(Tabla_Baterias[indice],true,false,false);
             return Tabla_Baterias[indice].tipo;
         }break;
         case 3:{                //funcion 1 Battery technology
             leetodo(Tabla_Baterias[indice],true,false,false);
             return Tabla_Baterias[indice].tecnologia;
         }break;
         case 4:{                //funcion 1 Battery charge
             ostringstream converter;
             leetodo(Tabla_Baterias[indice],false,true,false);
             converter << Tabla_Baterias[indice].carga;
             return converter.str();
         }break;
         case 5:{                //funcion 1 Battery state
             leetodo(Tabla_Baterias[indice],false,false,true);
             return Tabla_Baterias[indice].estado;
         }break;
     }
}

```

Greetsa, Branimir

This is a plug-in the function Get_Value(int index,string& udi) is called by the plug-in controller every mmm less that 10 times a second (I can control times).
maybe the problem is there, I try to refresh the information.
but maybe I doing something BAD there.

[COLOR="Red"]EDIT: I forgot to explain how this works:
main program run, and them loads the dynamic libs (like this one), the program calls init() function after loaded the lib successful,
next when is necessary the program call Get_Value with the function ID and the UDI to refresh the information and get the new value, that happen every time the program need the values[/COLOR]

---

### Post by MeduZa on 2009-01-30
> **nvteighen said:**
> Just a note. Have you used valgrind to detect the memory leak? (look for valgrind in the repos).

Use:
```

valgrind ./myprog

```

And post the output. You'll probably see a lot of "leaks" coming from GTK+ and related libraries, but don't worry.

yes I did, I install alleyoop (valgrind front end) but I don't understand the output

here the plugin starts working:

> 
Starting on the screen:2
==1384== 
==1384== Invalid write of size 1
==1384==    at 0x8051F9B: Socks::recive(std::string&) (socks.cpp:100)
==1384==    by 0x804AF86: lcd::RecvCommand() (lcd.cpp:103)
==1384==    by 0x804C5B1: lcd_writer::listen() (lcd_writer.cpp:205)
==1384==    by 0x8051725: main (lcdspicer.cpp:67)
==1384==  Address 0x444689f is 1 bytes before a block of size 1,024 alloc'd
==1384==    at 0x402505E: operator new[](unsigned) (vg_replace_malloc.c:268)
==1384==    by 0x8051F79: Socks::recive(std::string&) (socks.cpp:98)
==1384==    by 0x804AF86: lcd::RecvCommand() (lcd.cpp:103)
==1384==    by 0x804C5B1: lcd_writer::listen() (lcd_writer.cpp:205)
==1384==    by 0x8051725: main (lcdspicer.cpp:67)
==1384== 
==1384== Conditional jump or move depends on uninitialised value(s)
==1384==    at 0x80505F8: lcd_writer::RefreshScreen(int) (lcd_writer.cpp:187)
==1384==    by 0x8051870: main (lcdspicer.cpp:73)
==1384== 
==1384== Invalid write of size 1
==1384==    at 0x8051F9B: Socks::recive(std::string&) (socks.cpp:100)
==1384==    by 0x804AF86: lcd::RecvCommand() (lcd.cpp:103)
==1384==    by 0x8050665: lcd_writer::RefreshScreen(int) (lcd_writer.cpp:194)
==1384==    by 0x8051870: main (lcdspicer.cpp:73)
==1384==  Address 0x4448617 is 1 bytes before a block of size 1,024 alloc'd
==1384==    at 0x402505E: operator new[](unsigned) (vg_replace_malloc.c:268)
==1384==    by 0x8051F79: Socks::recive(std::string&) (socks.cpp:98)
==1384==    by 0x804AF86: lcd::RecvCommand() (lcd.cpp:103)
==1384==    by 0x8050665: lcd_writer::RefreshScreen(int) (lcd_writer.cpp:194)
==1384==    by 0x8051870: main (lcdspicer.cpp:73)
^C==1384== 
==1384== ERROR SUMMARY: 446 errors from 20 contexts (suppressed: 79 from 2)
==1384== malloc/free: in use at exit: 120,321 bytes in 1,188 blocks.
==1384== malloc/free: 9,627 allocs, 8,439 frees, 1,229,269 bytes allocated.
==1384== For counts of detected errors, rerun with: -v
==1384== searching for pointers to 1,188 not-freed blocks.
==1384== checked 277,148 bytes.

until here the program runs and I stopped it (^C==1384== ), the rest of valgrind is on a txt file attached

---

### Post by nvteighen on 2009-01-30
Hmm... take a look at the leak summary (after the ERROR SUMMARY). Take for example this case from your report:

```

==2887== 4 bytes in 1 blocks are still reachable in loss record 2 of 30
==2887==    at 0x40254FE: operator new(unsigned, std::nothrow_t const&) (vg_replace_malloc.c:244)
==2887==    by 0x403A26E: Init (system.cpp:180)
==2887==    by 0x805118A: plugin::Init_plugin(std::string&) (plugin.cpp:56)
==2887==    by 0x804A9CB: datos::LoadPlugin(int, std::string&) (datos.cpp:78)
==2887==    by 0x804BE58: lcd_writer::lcd_writer(std::string&) (lcd_writer.cpp:81)
==2887==    by 0x805144A: main (lcdspicer.cpp:45)

```

What you see there is the backtrace before a certain call to the new operator. There we see that it's the Init function in the module system.cpp which calls it, so the leak is produced by something created there.

Other cases of leaks are not your fault, but some library's. I see some due to GLib which you can't solve (but the GLib developers should)...

---

### Post by MeduZa on 2009-01-30
> **nvteighen said:**
> Hmm... take a look at the leak summary (after the ERROR SUMMARY). Take for example this case from your report:

```

==2887== 4 bytes in 1 blocks are still reachable in loss record 2 of 30
==2887==    at 0x40254FE: operator new(unsigned, std::nothrow_t const&) (vg_replace_malloc.c:244)
==2887==    by 0x403A26E: Init (system.cpp:180)
==2887==    by 0x805118A: plugin::Init_plugin(std::string&) (plugin.cpp:56)
==2887==    by 0x804A9CB: datos::LoadPlugin(int, std::string&) (datos.cpp:78)
==2887==    by 0x804BE58: lcd_writer::lcd_writer(std::string&) (lcd_writer.cpp:81)
==2887==    by 0x805144A: main (lcdspicer.cpp:45)

```

What you see there is the backtrace before a certain call to the new operator. There we see that it's the Init function in the module system.cpp which calls it, so the leak is produced by something created there.

Other cases of leaks are not your fault, but some library's. I see some due to GLib which you can't solve (but the GLib developers should)...

system.cpp is my first plugin, but that one don't increase the memory usage every loop (maybe that is an error that appear there because I stop the program and it never call the destructors to free the memory)
If I comment all the lines [COLOR="SeaGreen"]**leetodo(..)**[/COLOR] in the function string[COLOR="SeaGreen"]** Get_Value(int index,string& udi)**[/COLOR] the leak do not happen, that means that the leak is there or I'm implemented the dbus glib wrap in a wrong way.

Can some one explain me (or teach me) how the dbus_g_proxy_call works? I don't understand if this function get a value (you need to call it every time to get the new value) or hook a var to the g_main loop (and I only need to call dbus_g_proxy_call to hook my pointer / variable and glib refresh my value)

I really appreciate your help guys. Thanks

---

### Post by MeduZa on 2009-01-31
if someone like to test the program and look the memory leak only need to download the file from here:

[https://sourceforge.net/project/showfiles.php?group_id=242109&package_id=294735](https://sourceforge.net/project/showfiles.php?group_id=242109&package_id=294735)

is the 0.02, the 0.01 have no problems (and no battery plugin)

can someone explain me how dbus_g_proxy_call works (I already read documentation but like I can see something is not clear)?

---

### Post by MeduZa on 2009-02-01
no one? :(

nvteighen are you Argentinian?

(FreeTruco: An attempt to implement a card game in Scheme.) <<< esto te delato

---

### Post by nvteighen on 2009-02-01
> **MeduZa said:**
> no one? :(

I don't have a clue of how that could work... :p But actually, you shouldn't care: that's the idea of separating interface from implementation.

> 
nvteighen are you Argentinian?

(FreeTruco: An attempt to implement a card game in Scheme.) <<< esto te delato

Yes, though I'm living in Spain... That project has a bit of nostalgy in it...

---

### Post by MeduZa on 2009-02-01
> **nvteighen said:**
> I don't have a clue of how that could work... :p But actually, you shouldn't care: that's the idea of separating interface from implementation.



Yes, though I'm living in Spain... That project has a bit of nostalgy in it...

**dbus_g_proxy_call** updates the information automatically? because if**dbus_g_proxy_call** do that is easy to understand where is the problem.

---

