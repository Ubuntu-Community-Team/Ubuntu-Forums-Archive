---
title: "python-xmpp + gtalk"
date: 2008-11-26
forum: Programming Talk
---

### Post by dragobr on 2008-11-26
Hi! Kind of new here, hope someone can help me..

I was trying to build a simple google talk bot / client and started it with the python-xmpp lib.. I wrote the following:

```
#!/usr/bin/python
# -*- coding: ISO-8859-1 -*-

import sys,xmpp

def messageHandler(conex,msg):
    print "Remetente: " + str(msg.getFrom())
    print "Mensagem: " + str(msg.getBody())
    print msg

def main():
    if len(sys.argv) < 2:
        print "Sintaxe: python client.py <usuário> <senha>"
        sys.exit(0)

    # usuário e senha via argumentos
    gmail_user = sys.argv[1]
    gmail_pass = sys.argv[2]
    
    # servidor jabber
    gtalk_server = "talk.google.com"

    # seta parâmetros para conexão
    jid=xmpp.protocol.JID(gmail_user)
    cl=xmpp.Client(jid.getDomain()) # ,debug=[])

    # inicia conexão e tenta realizar login
    if not cl.connect((gtalk_server,5222)):
        raise IOError(1, "Não foi possível conectar ao servidor.")
    if not cl.auth(jid.getNode(),gmail_pass):
        raise IOError(2, "Houve um erro durante o login. O nome de usuário e a senha estão corretos?")

    # envia um "hi there"?
    cl.sendInitPresence()
    
    # handlers
    cl.RegisterHandler("message", messageHandler)    
    
    # envio de mensagem de teste
    cl.send( xmpp.Message( "contato@guribeiro.com.br" ,"teste" ) )
    
    # espera por eventos
    while 1:
        try:
            cl.Process(1)
        except KeyboardInterrupt:
            break
    
    cl.disconnect()

main()
```

But i cant seem to authenticate.. I've tried to use different accounts with, of course, the @gmail, and even without it, and nothing:

```
DEBUG: socket       got   <failure xmlns="urn:ietf:params:xml:ns:xmpp-sasl">
  <not-authorized/>
  </failure>
  </stream:stream>
DEBUG: dispatcher   ok    Got urn:ietf:params:xml:ns:xmpp-sasl/failure stanza
DEBUG: dispatcher   ok    Dispatching failure stanza with type-> props->[u'urn:ietf:params:xml:ns:xmpp-sasl'] id->None
DEBUG: sasl         error Failed SASL authentification: <not-authorized />
```

It's like I'm using a wrong username/password, but I'm not!

Can anyone give me a light on this one?

---

