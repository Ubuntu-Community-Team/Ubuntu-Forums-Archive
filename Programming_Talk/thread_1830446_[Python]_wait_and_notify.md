---
title: "[Python] wait and notify"
date: 2011-08-21
forum: Programming Talk
---

### Post by Frozen Forest on 2011-08-21
A program have two threads, one processing information and acts on it, the other only listen to a socket and deliver data received to the main thread. Data is shared between multiple hosts, when one host start sending should the other also start sending.

The intention of this code, is to send data every 5 s, but it can be sooner if the server socket receive data from another host. 
[PHP]
main_thread
class ServerSocket(socketserver.BaseRequestHandler):
    def handle(self):
        data = self.request[0].strip()
        global main_thread
        # store data
        main_thread.acquire()
        main_thread.notify()
        main_thread.release()

def main():
    global main_thread
    main_thread = threading.current_thread()
    
    client = ClientSocket()
    server = socketserver.UDPServer(('127.0.0.1', 22222), ServerSocket)
    threading.Thread(target=server.serve_forever).start()    

    while True:
        main_thread.acquire() # cause exception
        main_thread.wait(5)
        main_thread.release()

# Exception
AttributeError: '_MainThread' object has no attribute 'acquire'
[/PHP]EDIT:
Solved by changing to this, using python 3
```
main_thread = threading.Condition()
```

---

