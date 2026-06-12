---
title: "Occasional freeze reading SMS for HTML output"
date: 2009-08-27
forum: Programming Talk
---

### Post by UbuKunubi on 2009-08-27
Hello!

The python program included in this post runs on my ubuntu hardy home server - its task being to check for new SMS and write the messages into a HTML output file.

SOMETIMES - for whatever reason when I send the command AT+CPMS="SM","SM","SM" to get the number of new messages the returned string contains non-numerical data, in this case "SM", instead of just 1.

Mostly this program works fine but this occasional stumbling block is getting in the way of a reliable feature for my server.

I'd really appreciate any help, pointers, or advice with this.

Thanks in advance,
Ubu

```

# SMS.PY
 
import sys,time
import bluetooth  #Pybluez http://pybluez.googlecode.com
blah1=""
deviceName = "nokia 6000"
deviceAddress = "00:12:40:38:F6:75"
print 
print "Device name=",deviceName
print "Device addr=",deviceAddress
dunPort = 8 
foundDevices = bluetooth.discover_devices()
dunport=8
ooo=""
delcount=0
xnds=0
san=0
s = bluetooth.BluetoothSocket(bluetooth.RFCOMM)
print "Connecting to Phone now."
conn = s.connect((deviceAddress, dunPort))
while 1:
	iii=[]
	ndslinez=[]
	ndslines=[]
	san=san+1
	print "Run Count=",san,
	s.send("AT\r")
        ndstt= s.recv(1024)
        s.send("AT+CMGF=1\r")
        ndstt= s.recv(1024)
        s.send("AT+CNMI= 0,0,0,0,0\r")
        ndstt= s.recv(1024)
        ndstt= s.recv(1024)
	time.sleep(1)
        s.send('AT+CPMS="SM","SM","SM"\r')
        #print "1=", s.recv(1024)
	ndstt= s.recv(1024)
        msgcount = s.recv(1024)
        iii=msgcount.split(",")
	#print"message statuses"
	#print iii
	if (iii[-2].find('"SM"')== -1):
		smscount =int(iii[-2])
		delcount=smscount
		print "Have counted",smscount," of sms on sim card"
		start =0
		while start <> smscount:
			print"----->Reading from SMS index ",start
			cmd="AT+CMGR="+str(start)+"\r"
			s.send(cmd)
			triptest =s.recv(1024)
			#print "TRIP TESTING=",triptest
			if (len(triptest) > 25):
				ooo=triptest
			if (triptest.find("OK")== -1):
				print "OK NOT found."
				ooo = s.recv(1024)
			#print ooo
			ooo=ooo.replace("\nOK","")
			ooo=ooo.replace("\r","")
			ooo=ooo.replace("\n","")
			ooo=ooo.replace("<","&lt;")
			ooo=ooo.replace(">","&gt;")
			status =ooo[12:16]
			if (status.find("READ")!= -1):
				offset=57
				msg=ooo[offset:]
			if(status.find("UNRE")!= -1):
				offset=59
				msg=ooo[offset:]
			print msg
			nds=open("text.txt",'a')# this to log all the sms received
			nds.write(msg)
			nds.write("\n")
			nds.close()
			#print "==============DELETING the msg!"
			dcmd="AT+CMGD="+str(start)+"\r"
			print "DELTE cmd =",dcmd
			s.send(dcmd)
			print s.recv(1024)
			start=start+1

		nds=open("text.txt",'r')# this to log all the sms received
		ndslinez = nds.readlines()
		ndslinez.reverse()
		nds.close()
		ndslines = ndslinez[0:10]
		
		blah1='<html><head><meta http-equiv="refresh" content="15" > <title>Your Message Has been saved</title></head>'
		blah1 +='<BODY LANG="en-GB" BGCOLOR="#0066CC"><FONT COLOR="#ffffff"><font size="2">'
		blah1 += "</b><br><ol>" # and now the formatting for the list formatting in the page
		for z in ndslines:
			blah1 += z + "<br><br>"
		blah1 += "</ol></body> </html>"
		nds= open('qwerty.html', 'w')
		nds.write(blah1)
		nds.close()
		#s.close()
		print"Sleeping"
	time.sleep(5)

s.close()

```

---

