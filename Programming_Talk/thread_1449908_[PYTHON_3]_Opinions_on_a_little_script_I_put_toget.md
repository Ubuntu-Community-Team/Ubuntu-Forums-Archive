---
title: "[PYTHON 3] Opinions on a little script I put together."
date: 2010-04-08
forum: Programming Talk
---

### Post by pirateofms on 2010-04-08
I put this little script together to update a page on my hosted site with the external IP of my home network.  It's working fine, but I wanted some feedback about some things I may have done differently, or more efficiently. It's the first actually useful thing I've written, so don't be too harsh.

```
#!/usr/bin/python3

#update_server_ip.py
#Updates a webpage on a hosted server with the current external
#IP address.  Useful if your web hosting doesn't allow personal
#storage and you want friends to still be able to get to your 
#stuff on a local machine, without having to call you for the 
#IP every time.


from subprocess import getoutput
import ftplib
import urllib.request

#get current ip
def get_ip():
	'''Gets our current ip from ip.appspot.com'''
	print("Getting current ip address")
	cur_raw_ip = urllib.request.urlopen('http://ip.appspot.com').read()
	cur_ip = str(cur_raw_ip, encoding='utf-8')
	print("Done.")
	return(cur_raw_ip)

#upload our server_ip.html file to the server	
def do_upload():
	'''Upload file to the server'''
	print("Connecting to server...")
	server = ftplib.FTP('ftp.<address>.com', '<username>', '<password>')
	ip_file = open('server_ip.html','rb')
	print("Uploading 'server_ip.html'")
	server.storbinary('STOR server_ip.html', ip_file)
	ip_file.close()
	server.quit()
	print("Done.")

#Write out html file
def make_server_ip(cur_ip):
	'''Writes our html file'''
	print("Writing 'server_ip.html'")
	out_file = open('server_ip.html', 'wb')
	out_file.write(b'''
	<html>
		<head>
			<title>Server IP</title>
		</head>
		
		<body bgcolor=#000000 text=#f5f5f5>
		<center>
		<p>Chop's FTP Server:
		<p>''' + cur_ip + b'''
		</center>
		</body>
	</html>''')
	out_file.close()
	print("Done.")

def main():
	'''Just runs everything'''
	ip_addr = get_ip()
	make_server_ip(ip_addr)
	do_upload()

main()
```

---

### Post by HellBoz on 2010-04-08
Why do you need cur_ip ( get_ip () ) if you never actually use/return it ? :confused:

---

### Post by pirateofms on 2010-04-08
glad you pointed that out.  It was before I figured out that I needed to pass everything as byte data, I just forgot to take it out.

---

