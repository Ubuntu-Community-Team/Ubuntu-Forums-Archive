---
title: "python socket client"
date: 2010-07-15
forum: Programming Talk
---

### Post by b4nsh33 on 2010-07-15
Hello to all, im trying to connect to a remote service running on port 15143, googling around i found sveral examples and i have coded this:

def opensocket(ipaddr, port, mode):
    # create the socket
    skt = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    # open the socket
    try:
		skt.setblocking(mode)
		skt.settimeout(300)
		skt.connect((ipaddr, port))
    except socket.error, e:
        print "Failed to connect to server %s %d %d" % (ipaddr, port, mode)
        print "Error %s" % (e.args[0])
        print "Goodbye..."
        sys.exit()

	return(skt)


def dac_execute(dac_stream, msg):
    print "antes de enviar"
    dac_stream.send(msg)

dac_stream = opensocket(DACSERVER, DACPORT, BLOCKING)
print "entro loco"
resultado = dac_execute(dac_stream, '2000600000001F9D')


when i run this script i got the error:

Traceback (most recent call last):
  File "dac_wirelink.py", line 65, in <module>
    resultado = dac_execute(dac_stream, '2000600000001F9D')
  File "dac_wirelink.py", line 41, in dac_execute
    dac_stream.send(msg)
AttributeError: 'NoneType' object has no attribute 'send'


im passing dac_stream to the dac_execute function but it is not working, what it is wrong with my code?
thanks in advance for any help

---

### Post by dwhitney67 on 2010-07-15
Perhaps the issue you are having is because you did not import the socket module?  Or perhaps because you did not indent your code properly?

I tested your code, with some additional "frills" added, and it worked fine.

```

import socket

def opensocket(ipaddr, port, mode):
        # create the socket
        skt = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

        # open the socket
        try:
                skt.setblocking(mode)
                skt.settimeout(300)
                skt.connect((ipaddr, port))
        except socket.error, e:
                print "Failed to connect to server %s %d %d" % (ipaddr, port, mode)
                print "Error %s" % (e.args[0])
                print "Goodbye..."
                sys.exit()

        return(skt)


def dac_execute(dac_stream, msg):
        print "antes de enviar"
        dac_stream.send(msg)

dac_stream = opensocket("127.0.0.1", 9000, 1)
print "entro loco"
resultado = dac_execute(dac_stream, '2000600000001F9D')

```

---

### Post by b4nsh33 on 2010-07-15
you rock dwhitney, the indentation was the culprit, thanks a lot

---

