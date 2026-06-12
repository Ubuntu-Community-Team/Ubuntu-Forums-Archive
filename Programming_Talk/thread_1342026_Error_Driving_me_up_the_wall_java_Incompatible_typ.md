---
title: "Error Driving me up the wall: java: Incompatible types."
date: 2009-11-30
forum: Programming Talk
---

### Post by MCBTunes on 2009-11-30
I am getting an incompatible types error on my client side trying to call a method that sends a SOAP request.I was originally having the getChat method return a String[] but I was getting the same error. Thoughts? I could really use the help.

Thanks.

Note* temp on the client side is a String and rooms is a hash table with a string key and int value.

```

client/Client.java:164: incompatible types
found   : java.util.List<java.lang.String>
required: java.util.LinkedList<java.lang.String>
				fromServer = chatProxy.getChat(temp, 0/*rooms.get(temp)*/);
				                              ^
1 error


```

Code that sends the request:
```

LinkedList<String> fromServer = new LinkedList<String>(); 


for(i=0; i<roomNames.size();i++){
	temp = roomNames.get(i);
	fromServer = chatProxy.getChat(temp, rooms.get(temp));
	if(!fromServer.get(0).equals("Error")){
		if(!fromServer.get(0).equals("")){
			System.out.println(temp2);
			rooms.remove(temp);
			rooms.put(temp, 1 + (Integer.parseInt(fromServer.get(1))));
		}
	}
}

```

Server side:
```

@WebMethod
public LinkedList<String> getChat(String roomName, int id){
	LinkedList<String> temp = new LinkedList<String>();
	
	if(roomNameExists(roomName)){
		ChatRoom tempRoom = getRoom(roomName);
		temp.add(tempRoom.toString(id));			
		temp.add(Integer.toString(tempRoom.getID()));
		//temp[0] = tempRoom.toString(id);
		//temp[1] = Integer.toString(tempRoom.getID());
	}
	else{
		temp.add("Error");			
		//temp[0] = "Error";
	}

	return temp;


```

---

### Post by doas777 on 2009-11-30
cast it?

---

