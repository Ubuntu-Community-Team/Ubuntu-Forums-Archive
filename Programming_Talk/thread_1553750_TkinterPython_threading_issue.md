---
title: "Tkinter/Python threading issue"
date: 2010-08-15
forum: Programming Talk
---

### Post by Lysander10 on 2010-08-15
Hello,

I'm using Ubuntu 10.04 and Python 2.6.5, and learning Tkinter, and I have an issue that I'd appreciate help with. I have a program that initializes a GUI (I'll call this the "GUI process"), then spawns another process that listens on a network via the TCP/IP protocol for incoming strings (I'll call this the "server process"). Everything works well up to this point.

What I want to happen next is for the server process to update a label in the GUI process when it receives a message from the network. First I tried passing a control variable for the label's text into the server process, but when I updated the control variable, nothing happened(no error messages, no feedback of any kind).

I tried piping the message from the server process into the GUI process using os.write() and os.read() - and this works, but not the way I need it to. I need the label to be updated automatically, without any intervention from the user (at the moment, it only works when the user clicks an "Update" button). I tried having the GUI process check the pipe for messages automatically, but when I do this it hangs when there's nothing in the pipe.

I've tried other avenues as well, but probably nothing worth mentioning. If you have any suggestions, I would be very grateful.

---

### Post by Lysander10 on 2010-08-15
I'll try posting some of the code, to help better illustrate what I'm talking about.

---

### Post by Lysander10 on 2010-08-15
```
class MessageServer:
    '''Creates a message server object that listens for textual information
       and sends it back to the main program. Intended to be spawned as a
       separate process.
       '''
    
    def __init__(self, port_number, server_send, server_receive):
        '''@param server_send The pipe MessageServer uses to send text back to the main program.
           @param port_number The port the server listens on the network at.
           '''
    
        self.server_send = server_send
        self.server_receive = server_receive
        self.client_socket = None
        self.address = None

        self.error_logger = errorlogger.ErrorLogger(program_name=PROGRAM_NAME)

        self.server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        self.server_socket.bind(('localhost', port_number))
        self.server_socket.listen(1)

        self.listen()

    def listen(self):
        # listen for messages until process is killed
        # if a message is received, send it back to the main program
        (self.client_socket, self.address) = self.server_socket.accept()
        while True:
            input_stream = str(self.client_socket.recv(1024))
            if len(input_stream) != 0:
                os.write(self.server_send, input_stream)
                input_stream = None
```

---

### Post by Lysander10 on 2010-08-15
```
    def check_message(self, spawn=True):
        '''Method for pulling message from server process.'''

        if spawn: self.pid2 = os.fork()
        if self.pid2 == 0:
            if verbose: print('message checker initialized')
            # repeat message check forever
            while True:
                incoming_data = os.read(self.client_receive, 1024)
                if verbose: print('Message receive successful')
                if verbose: print('Message: ' + incoming_data)
                self.update_messages(incoming_data)
```

---

### Post by Lysander10 on 2010-08-15
```
    def update_messages(self, new_text=False):
        '''Adds new string to conversation box.
           @param new_text The string to be added.
           '''

        if not new_text: new_text = INCOMING_DATA
        try:
            current_text = self.chat_text.get()
            current_text += '\n' + new_text
            self.chat_text.set(current_text)
```

---

### Post by Lysander10 on 2010-08-15
What happens when I try this is the server receives messages from the network just fine, and the check_message thread receives them from the server just fine, but the GUI widget isn't being updated when self.chat_text.set() is called. I presume this is because I'm trying to update it from a different thread, which is what I'm having trouble figuring out how to do.

---

### Post by Lysander10 on 2010-08-15
Well, I figured it out...

---

