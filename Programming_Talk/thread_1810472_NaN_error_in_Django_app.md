---
title: "NaN error in Django app"
date: 2011-07-23
forum: Programming Talk
---

### Post by kcode on 2011-07-23
I am developing a Django app.
A part of app is exchange of numbers between client and server. But when client data is sent to server, web server complains about NaN. Its output is this - 
```

23/Jul/2011 14:34:36] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:36] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:39] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:39] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:42] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:42] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:45] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:45] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:48] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:48] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:51] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:51] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:54] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:54] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:57] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:57] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:35:00] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:35:00] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374

```

Code on the client side that sends number is - 
```

var client_pl_token=0;
function fetch_pl(){
    var data = 'client_pl_token='+Number(client_pl_token);

    $.get('playlist_updated', data, 
	function(data){
	    alert(data);
	    if(data != 'Playlist is up to date.'){
		var patt = /\d+$/;
		client_pl_token = Number(parseInt(data.match(patt)));
		//if(isNaN(clienet_pl_token)) alert('NaN error!');
		//alert(data);
		setTimeout('', 2000);
		var code = data.substring(0,data.search(patt));
		update_gp(code);
	    }
	    else{
		$('#nfc').html(data);
	    }
	}, 'text');
    setTimeout('fetch_pl()', 3000);
}

```

Problem is that sometimes it work and sometimes it doesn't.
Let me know if you want any more information.

Thanks
kcode

---

### Post by Arndt on 2011-07-23
> **kcode said:**
> I am developing a Django app.
A part of app is exchange of numbers between client and server. But when client data is sent to server, web server complains about NaN. Its output is this - 
```

23/Jul/2011 14:34:36] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:36] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:39] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:39] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:42] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:42] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:45] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:45] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:48] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:48] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:51] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:51] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:54] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:54] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:34:57] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:34:57] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374
[23/Jul/2011 14:35:00] "GET /playlist_updated?client_pl_token=NaN HTTP/1.1" 500 62199
[23/Jul/2011 14:35:00] "GET /playlist_updated?client_pl_token=0 HTTP/1.1" 500 72374

```

Code on the client side that sends number is - 
```

var client_pl_token=0;
function fetch_pl(){
    var data = 'client_pl_token='+Number(client_pl_token);

    $.get('playlist_updated', data, 
	function(data){
	    alert(data);
	    if(data != 'Playlist is up to date.'){
		var patt = /\d+$/;
		client_pl_token = Number(parseInt(data.match(patt)));
		//if(isNaN(clienet_pl_token)) alert('NaN error!');
		//alert(data);
		setTimeout('', 2000);
		var code = data.substring(0,data.search(patt));
		update_gp(code);
	    }
	    else{
		$('#nfc').html(data);
	    }
	}, 'text');
    setTimeout('fetch_pl()', 3000);
}

```

Problem is that sometimes it work and sometimes it doesn't.
Let me know if you want any more information.

Thanks
kcode

Give an example of what's in 'data' when NaN results. When you say "sometimes", do you mean that the same data sometimes gives NaN and sometimes not?

---

### Post by kcode on 2011-07-23
In case of NaN, no data is sent by the server. 

I have changed the data exchange method between c/s to xml. NaN still comes intermittently, but it is not causing problem. Don't know why.

---

### Post by kcode on 2011-08-05
I solved the problem by doing data transaction in XML format.

---

