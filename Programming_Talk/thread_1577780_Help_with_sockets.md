---
title: "Help with sockets"
date: 2010-09-19
forum: Programming Talk
---

### Post by psychok7 on 2010-09-19
hi.. i have been playing around with sockets for a school project and im trying to send an object from the client to the the server but im having this IO:"java.io.WriteAbortedException: writing aborted; java.io.NotSerializableException: java.io.ObjectOutputStream" error. but the thing is my class MESSAGE implements serializable so i guess i am doing somthing else wrong. can anyone help me? 

here is the some of the code, let me know if you need more

Server side:
```
    public Connection (Socket aClientSocket, int numero) {
        thread_number = numero;
        try{
            clientSocket = aClientSocket;
            in = new DataInputStream(clientSocket.getInputStream());
            out = new DataOutputStream(clientSocket.getOutputStream());
            this.start();
        }catch(IOException e){System.out.println("Connection:" + e.getMessage());}
    }
    //=============================
    @Override
    public void run(){
        String resposta;
        Message receiveobject = null;
        try {
            ois = new ObjectInputStream(in);
        } catch (IOException ex) {
            Logger.getLogger(Connection.class.getName()).log(Level.SEVERE, null, ex);
        }
        try{
            while(true){
                //an echo server
                //String data = in.readUTF();
                
                try {
                    receiveobject = (Message) ois.readObject();
                } catch (ClassNotFoundException ex) {
                    Logger.getLogger(Connection.class.getName()).log(Level.SEVERE, null, ex);
                }

                System.out.println("T["+thread_number + "] Recebeu: "+receiveobject.getText());
                resposta=receiveobject.getText().toUpperCase();
                out.writeUTF(resposta);
            }
        }catch(EOFException e){System.out.println("EOF:" + e);
        }catch(IOException e){System.out.println("IO:" + e);}
    }
```

CLIENT SIDE:
```
	    DataInputStream in = new DataInputStream(s.getInputStream());
	    DataOutputStream out = new DataOutputStream(s.getOutputStream());

	    String texto = "";
	    InputStreamReader input = new InputStreamReader(System.in);
	    BufferedReader reader = new BufferedReader(input);
	    System.out.println("Introduza texto:");

            Message msg;
            ObjectOutputStream oos = new ObjectOutputStream(out);
	    // 3o passo
	    while (true) {
		// READ STRING FROM KEYBOARD
		try {
		    texto = reader.readLine();
		} catch (Exception e) {
		}

                msg=new Message(s.toString(),texto);
                oos.writeObject(oos);
               // oos.reset();
             //   System.out.println("tesste"+s.toString());
		// WRITE INTO THE SOCKET
		//out.writeUTF(s.toString());

		// READ FROM SOCKET
		String data = in.readUTF();

		// DISPLAY WHAT WAS READ
		System.out.println("Received: " + data);
	    }
```

---

### Post by Some Penguin on 2010-09-19
Doesn't matter if you labeled it as implementing Serializable or not.  Ask yourself whether the member field in question itself implements Serializable and what exactly you expect it to do, when you tell it to serialize such a thing.

---

### Post by psychok7 on 2010-09-19
> **Some Penguin said:**
> Doesn't matter if you labeled it as implementing Serializable or not.  Ask yourself whether the member field in question itself implements Serializable and what exactly you expect it to do, when you tell it to serialize such a thing.

sorry i didnt really understand what you said..so wht am i supposed to do?

---

### Post by Some Penguin on 2010-09-19
*Understand*.  That is the point.  Ask yourself what it would really mean to serialize something with a stream inside, and you'll understand what caused the problem.

---

### Post by psychok7 on 2010-09-21
after resting for 2 days i gave another look to the code and after 3min found out the problem. 


```
 msg=new Message(s.toString(),texto);
                oos.writeObject(msg);
```

---

