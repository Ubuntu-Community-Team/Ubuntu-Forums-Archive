---
title: "[C++] zeromq thread safte closing"
date: 2013-06-07
forum: Programming Talk
---

### Post by giane on 2013-06-07
Hi all 
I have a problem for closing a thread that implements the subscription side of a pub-sub pattern; I'm using zeromq 3.2 version.
The code that implements the thread is:
```

ppsock->setsockopt(ZMQ_SUBSCRIBE, "001", 1);
    
    while (!thread_stop)
    {
        messaggio.clear();
        messaggio = s_recv(*ppsock);
        risposta.clear();
        risposta = s_recv(*ppsock);
        cout << risposta << endl;
        tok.clear();
        boost::split(tok, risposta, boost::is_any_of(";"));
        i = 0;
        for (vector<std::string>::iterator beg = tok.begin(); beg != tok.end(); ++beg)
        {
            //cout << std::to_string(i) << ": " << *beg << "\n";
            switch (i)
            {
            case 0:
            {
                codice = std::stol(*beg);
                break;
            }
            case 1:
            {
                cmd = *beg;
                break;
            }
            default:
            {
                if (codice == ce_id)
                {
                    if ((zone[i - 2] != std::stoi(*beg))&&(std::stoi(*beg) != -1))
                    {
                        zone[i - 2] = std::stoi(*beg);
                        sigZona(ce_id, i - 2);
                        itv = listacomandi.find(i-2);
                        if(itv!=listacomandi.end())
                        {
                            cout<<"Trovato comando su zona "<<std::to_string(itv->first)<<"Tipo: "<<std::to_string(itv->second)<<endl;
                            if(itv->second == 1)
                            {
                                if (zone[i-2] == 1)
                                {
                                    signComando(ce_id, 10, itv->first, 1, 1);
                                }
                            }
                            if(itv->second == 2)
                            {
                                if (zone[i-2] == 0)
                                {
                                    signComando(ce_id, 10, itv->first, 2, 1);
                                }
                            }
                        }
                    }
                }
            }
            }
            i++;
        }
        if (!comandi.empty())
        {
            Urmet::eseguiComando();
        }

```
For closing the thread I set the thread_stop variable and the join function. the problem is that s_recv function is blocking and i need to wait the next message for closing.
Someone know a method for make s_recv non bloking or close subscription socket safety.
Thanks

---

### Post by dwhitney67 on 2013-06-07
From what I have Googled (btw, you could have done this too!), it would appear that zmq_poll() is the favored means of controlling the blocking call to zmq_recv().  Of course, one could set the call to non-blocking using the flag, but that may be too extreme for your case.

You can read about zmq_poll() here:  [http://api.zeromq.org/2-1:zmq-poll](http://api.zeromq.org/2-1:zmq-poll)

Here's an example:
```

zmq_pollitem_t items [] = { { socket,  0, ZMQ_POLLIN, 0 } };
int rc = zmq_poll (items, 1, timeout * ZMQ_POLL_MSEC);

...

int status = zmq_recv(...);

if (status == -1)
    // no message
else
    // got something

```

P.S.  Where did you dig up s_recv()?  I found a single reference to it while Googling, but nothing about it in the [ZeroMQ API]("http://api.zeromq.org/").

---

