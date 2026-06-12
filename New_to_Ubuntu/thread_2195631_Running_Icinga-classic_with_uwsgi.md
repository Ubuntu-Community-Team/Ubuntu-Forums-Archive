---
title: "Running Icinga-classic with uwsgi?"
date: 2013-12-25
forum: New to Ubuntu
---

### Post by strowi on 2013-12-25
Hi,

i have been running icinga-classic with fastcgi for a while now. But on a different server i am already using uwsgi-cgi for other applications.
Can anyone give me some hints on configuring nginx+uwsgi for this? I seem to be missing some path/permission configuration. The html-part/menu loads fine, but the cgi has problems:

icinga:
```

url_html_path=/
...

```

uwsgi-ini:
```

[uwsgi]
plugins = cgi
uid = www-data
gid = www-data
cgi-allowed-ext = .cgi
cgi = /usr/lib/cgi-bin/icinga/;

```

nginx-conf:
```

server {
        listen XXX:443 ssl;
        listen XXX:443 ssl;

        server_name xyz.de;

	include /etc/nginx/conf/ssl.conf;
#	include /etc/nginx/conf.d/*.conf;

        access_log /var/www/vhosts/XXX/log/status.access.log;
        error_log /var/www/vhosts/XXX/log/status.error.log error;

	auth_basic "Nagios Restricted Access";
        auth_basic_user_file /etc/nagios3/htpasswd.users;

	location /stylesheets {
        	root /etc/icinga;
	}
	location /images {
		root /usr/share/icinga/htdocs/;
	}

	location / {
		root /usr/share/icinga/htdocs;
		rewrite ^/$ /index.html permanent;
	}


	location ~ (.*)\.cgi$ {
        	root /usr/lib/cgi-bin/icinga;
	        rewrite ^/cgi-bin/(.*)\.cgi /$1.cgi break;
	        include /etc/nginx/uwsgi_params;

	        uwsgi_pass  unix:/var/run/uwsgi/app/nagios/socket;
		uwsgi_param SCRIPT_NAME $1.cgi;
		uwsgi_modifier1 9;
	}
	
}

```

On the website it shows "Bad Gateway" so it has to be somewhere between nginx/uwsgi. The uwsgi-logs show 

[pid: 31970|app: -1|req: -1/1]  () {46 vars in 806 bytes} [Wed Dec 25 17:32:23 2013] GET /tac.cgi => generated 0 bytes in 0 msecs (HTTP/1.1 404) 0 headers in 35 bytes (0 switches on core 0)
[pid: 31969|app: -1|req: -1/2]  () {46 vars in 806 bytes} [Wed Dec 25 17:32:24 2013] GET /tac.cgi => generated 0 bytes in 0 msecs (HTTP/1.1 404) 0 headers in 35 bytes (0 switches on core 0)

Which tells me that everything goes to uwsgi as planned, but uwsgi seems to be unable to find the cgi?

Any tips?

thx in advance!

greetings,
strowi

---

### Post by strowi on 2013-12-28
Found the solution/error myself and documented: ;)
[http://wiki.hasnoname.de/doku.php?id=nginx:icinga](http://wiki.hasnoname.de/doku.php?id=nginx:icinga)

---

