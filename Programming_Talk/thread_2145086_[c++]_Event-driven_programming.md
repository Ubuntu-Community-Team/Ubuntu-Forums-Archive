---
title: "[c++] Event-driven programming"
date: 2013-05-14
forum: Programming Talk
---

### Post by giane on 2013-05-14
Hi all.
I have a problem. I'm developing a program in c++ that controls the state of an input using a polling cycle and when the state changes i need to comunicate to another class/thread that sends a message on a socket connection.
Now i need a mechanism to comunicate that the state is changed and i'm thinking using events but i haven't found much documentation on how can I implement the event in C++ and the documentation that i found is not clear.
Can someone explain me how i can implement the event-driven mechanism or can link me some site?
Thank you and sorry for my english

---

### Post by TheFu on 2013-05-14
If you are doing threaded programming, then you need to use thread-safe methods to communication between different threads. This is very important. How to accomplish that is an advanced topic best addressed with a mentor and advanced UNIX C++ programming book.  I'd probably use shared memory myself, but that is without knowing anything about your specific program and requirements. There are other ways, like using named pipes, that might be more suitable too. It all depends on the situation.

BTW, I'd probably have that polling code run on a different thread than the main program and spawn a worker thread to handle the new event processing if that processing is long running - anything over 10 seconds.

The C++ language doesn't support multithreading directly, at least it didn't in the older standard version.  Someone with a Java background might expect that.  A websearch for "multithreaded C++ howto" found many relevant links.

---

### Post by giane on 2013-05-14
I think that I'm a quite well programmer  and I develop the program exactly as you describe. I have a class called "Central" that implements a Run method(a thread) where I'm connecting to an hardware like Arduino and constantly reads the value of an input.
There is another class called "Server" that implements a Run method (another thread) that talk with a Jboss application.
Now i need that "Central", when the state changes, notify to "Server" that the state changed. Sure I can implement a list of struct  where I storage the state changing and the "Server" can read from this list but i think is not real efficent. I post the class header.
Sorry for the Italian documentation.
Server.h
```

#ifndef SERVER_H
#define SERVER_H
#include <thread>
#include <string>
#include <iostream>
#include <string.h>
#include <mutex>
#include <atomic>

#include "Socket.h"
#include "SocketException.h"
#include "database.h"
#include "parametri.h"
#include "logger.h"
#include "define.h"

/**
* \struct manage_thread
* \brief Questa struct permette di tenere traccia di quali thread sono attivi visto che i thread sono detached
*/
struct manage_thread
{
    thread t;
    bool attivo;
};

/**
* \class Server
* \brief Questa classe crea un server in ascolto su una porta e ne gestisce le eventuali connessioni
* Viene usato come connessione tra il client E-pro e la telegestione delle diverse centrali
*/
class Server
{
public:

    /**
    *\brief Costruttore della classe
    */
    Server ();
    /**
    *\brief Distruttore della classe
    */
    virtual ~Server();
    /**
    *\brief Metodo che fa partire il server
    */
    void Start();
    /**
    *\brief Metodo che ferma il server
    */
    void Stop();
    /**
    *\brief Metodo che imposta il segnale di spegnimento del server e attende il completamento delle operazioni
    */
    void WaitForCompletation();

private:
    /**
    *\brief Metodo che implementa la routine del server e lo pone in ascolto sulla porta specificata nel file di configurazione
    */
    void Run ();

    /**
    *\brief Metodo che viene richiamato nel caso di una nuova connessione sul server principale e gestisce le richieste.
    */
    void serviceRoutine(Socket new_sock, int n_thread);

    /**
    *\brief Metodo che inserisce o disinserisce una partizione
    *\param stato se <b>true</b> inserisce se <b>false</b> disinserisce
    *\param nelem indica il numero dell'elemento sul quale effettuare l'operazione.
    *\param centrale puntatore alla centrale sulla quale eseguire l'operazione.
    *\return <b>true</b> se l'operazione ha avuto successo <b>false</b> altrimenti
    */
    bool inserisciArea(bool stato, int nelem, Centrale * centrale);

    /**
    *\brief Metodo che include o esclude una zona
    *\param stato se <b>true</b> esclude se <b>false</b> include
    *\param nelem indica il numero dell'elemento sul quale effettuare l'operazione.
    *\param centrale puntatore alla centrale sulla quale eseguire l'operazione.
    *\return <b>true</b> se l'operazione ha avuto successo <b>false</b> altrimenti
    */
    bool escludiZona(bool stato, int nelem, Centrale * centrale);

    /**
    *\brief Metodo che include o esclude un programmatore orario
    *\param stato se <b>true</b> esclude se <b>false</b> include
    *\param centrale puntatore alla centrale sulla quale eseguire l'operazione.
    *\return <b>true</b> se l'operazione ha avuto successo <b>false</b> altrimenti
    */
    bool escludiProgrammatore(bool stato, Centrale * centrale);
private:
    Database * db_epro;
    Parametri * param;
    Logger * log;
    Socket serversock;
    thread mainthread;
    manage_thread thread_serventi[10];
    mutex mut;
    atomic<bool> thread_stop;
};

#endif // SERVER_H

```
Centrale.h
```

#ifndef CENTRALE_H
#define CENTRALE_H
#include <string>
#include <iostream>
#include <sstream>
#include <thread>
#include <postgresql/libpq-fe.h>
#include <atomic>
#include <mutex>

#include "define.h"
#include "comandi.h"
#include "parametri.h"
#include "database.h"
#include "logger.h"

using namespace std;

/**
*\class Centrale "centrale.h"
*\brief Classe astratta che rappresenta i diversi tipi di centrale da telegestire
*/
class Centrale
{
public:
    /**
    *\brief Costruttore della classe
    *\param [in] codice contiene il <b>ce_id</b> della centrale
    */
    Centrale (long codice);
    /**
    *\brief Distruttore della classe
    */
    virtual ~Centrale();
    /**
    *\brief Metodo che restituisce lo stato delle zona passata come parametro.
    *\param [in] nzona indica il numero della zona della quale si vuole lo stato.
    *\return ritorna un byte con i seguenti campi: bit 0 allarme bit 1 inclusa bit 2 tamper
    */
    char getStatoZone (int nzona);
    /**
    *\brief Metodo che restituisce lo stato della partizione passata come parametro
    *\param [in] npartizione indica il numero della partizione della quale si vuole conoscere lo stato
    *\return un byte che contiene lo stato della partizione: bit 0 allarme bit 1 inseritmento tot bit 2 inserimento parziale
    */
    char getStatoPartizioni (int npartizione);
    /**
    *\brief Metodo che restituisce lo stato della centrale
    *\return un byte che contiene lo stato della centrale: bit 0 tamper bit 1 mancanza 220V tot bit 2 batteria bassa
    */
    char getStatoCentrale ();
    /**
    *\brief Metodo che restituisce lo stato del programmatore passato come parametro
    *\return <b>true</b> se il programmatore è attivo <b>false</b> se il programmatore non è attivo
    */
    bool getStatoProgrammatore ();
    /**
    *\brief Metodo per inserire o disinserire la partizione passata come parametro
    *\param [in] npartizione Numero della partizione sulla quale applicare il comando
    *\param [in] stato Contiene il tipo di comando da eseguire
    *\return <b>1</b> in caso di successo <b>0</b> altrimenti
    */
    int setStatoPartizione (int npartizione, enum_Comandi stato);
    /**
    *\brief Metodo per includere o escludere la zona passata come parametro
    *\param [in] nzona Numero della zona sulla quale applicare il comando
    *\param [in] stato Contiene il tipo di comando da eseguire
    *\return <b>1</b> in caso di successo <b>0</b> altrimenti
    */
    int setStatoZona (int nzona, enum_Comandi stato);
    /**
    *\brief Metodo per bloccare o sbloccare un programmatore orario passata come parametro
    *\param [in] stato Contiene il tipo di comando da eseguire
    *\return <b>1</b> in caso di successo <b>0</b> altrimenti
    */
    int setProgrammatoreOrario (enum_Comandi stato);
    /**
    *\brief Metodo per impostare il codice della centrale
    *\param [in] codice Contiene il codice della centrale
    *\return <b>1</b> in caso di sucesso <b>0</b> altrimenti
    */
    int setCodiceCentrale (long codice);

    /**
    *\brief Metodo che dovrà essere essere implementato da le classi che estendono questa classe
    */
    virtual void Run () = 0;
    /**
    *\brief Metodo che fa partire il thread
    */
    void Start();
    /**
    *\brief Metodo che ferma il thread
    */
    void Stop();
    /**
    *\brief Metodo che ferma il thread e attende la sua chiusura
    */
    void WaitForCompletation();
    /**
    *\brief Metodo per testare se il thread è vivo
    *\return <b>true</b> se il thread è attivo <b>false</b> altrimenti
    */
    bool isAlive();

protected:
    Database * db_epro;
    Parametri * param;
    Logger * log;
    atomic<char> zone[513];
    atomic<char> partizioni[33];
    atomic<char> centrale;
    atomic<bool> programmatore;
    long codiceCentrale;
    list<Comandi> comandi;
    bool thread_stop;
    std::thread t1;
    string query;
    std::mutex m;
    stringstream s;
    string messaggio;
    int timeout;
};

#endif // CENTRALE_H

```

---

### Post by SledgeHammer_999 on 2013-05-14
Disclaimer: I haven't read your code snippets

You can take a look at [Boost.Signals](http://www.boost.org/doc/libs/1_53_0/doc/html/signals.html) and [Boost.Signals2](http://www.boost.org/doc/libs/1_53_0/doc/html/signals2.html). The second one is a thread safe version of the first one. These are 2 of the few C++ event/signal implementations. Another one is [libsigc++](http://libsigc.sourceforge.net/)(used by Gtkmm mostly, but independent).

---

### Post by giane on 2013-05-20
At the end i used the Signal2 library my software pass from some second for refresh the state of the input to a real time refresh :O
Thank you all

---

