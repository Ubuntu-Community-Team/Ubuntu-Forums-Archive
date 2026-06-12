---
title: "Javascript Websocket server message broadcast to clients"
date: 2015-11-22
forum: Programming Talk
---

### Post by Blackbug on 2015-11-22
[FONT=Arial]I am trying to create a dummy websocket server in javascript to send some message to my android client app. The messages will be injected to the server using a html page( javascript ), which will further be passed on to the android client. I am able to connect these two clients (web and android) individually with the server, however, unable to achieve the flow I want, i.e. Web based javascript sends message to running Nodejs websocket server, which broadcast this message to the android client.[/FONT]
[FONT=Arial]This is the code I am using for server side

```
[FONT=Verdana]var WebSocketServer = require("ws").Server;[/FONT]
```[/FONT]```

var http = require("http");
var express = require("express");
var port = 2001;


var app = express();
app.use(express.static(__dirname + "/../"));
app.get('/someGetRequest', function(req, res, next) {
  console.log('receiving get request');
});
app.post('/somePostRequest', function(req, res, next) {
  console.log('receiving post request');
});
app.listen(80); //port 80 need to run as root


console.log("app listening on %d ", 80);


var server = http.createServer(app);
server.listen(port);


console.log("http server listening on %d", port);


var userId;
var wss = new WebSocketServer({
  server: server
});
wss.on("connection", function(ws) {
  console.info("websocket connection open");


  var timestamp = new Date().getTime();
  userId = timestamp;


  ws.send(JSON.stringify({
    msgType: "onOpenConnection",
    msg: {
      connectionId: timestamp
    }
  }));




  ws.on("message", function(data, flags) {
    console.log("websocket received a message");
    var clientMsg = data;


    ws.send(JSON.stringify({
      msg: {
        connectionId: userId
      }
    }));
    console.log(clientMsg);


  });


  ws.on("close", function() {
    console.log("websocket connection close");
  });
});
console.log("websocket server created");



```[FONT=Arial]


Webclient:

```
[FONT=Verdana]< script type = "text/javascript" >[/FONT]
```[/FONT]```

  var websocketURL = 'ws://localhost:2001/';


function startWebSocket() {
  try {
    ws = new WebSocket(websocketURL);
  } catch (e) {
    alert("Unable to connect to webserver")
  }
}


function sendMessage(text) {
  var message = 'Test message from webclient: ' + text;
  ws.send(message);
  alert(message);
}


startWebSocket(); < /script>
        
        <button onclick="sendMessage('From button1')">Button 1</button > < br >
[FONT=Arial][FONT=Verdana]  < button onclick = "sendMessage('From button2')" > Button 2 < /button><br>[/FONT][/FONT]
```[FONT=Arial]


Android client is using simple Socket class and its methods for post processing

```
s = new Socket(HOST, TCP_PORT);
```

Please suggest if anyone has any idea how I can route the message from web client to my android client via websocket server. I am using nodejs.[/FONT]

---

### Post by PaulM1985 on 2015-11-23
I have had a quick search online and it looks like the socket.io module is what you need to do this. Below is a link to an example tutorial.  Hopefully you can take what you need from that to get set up:
[http://psitsmike.com/2011/09/node-js-and-socket-io-chat-tutorial/](http://psitsmike.com/2011/09/node-js-and-socket-io-chat-tutorial/)

---

