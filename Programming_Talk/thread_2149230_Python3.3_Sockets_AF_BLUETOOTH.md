---
title: "Python3.3 Sockets AF_BLUETOOTH"
date: 2013-05-28
forum: Programming Talk
---

### Post by ki4jgt on 2013-05-28
When creating an AF_BLUETOOTH socket, does one need to connect to the receiving server before sending or can one simply send the data?

---

### Post by epicoder on 2013-05-28
Although I'm not too familiar with Bluetooth, I'm pretty sure any socket made with socket.socket uses the same abstraction. You need to connect first with socket.connect before using socket.send and socket.recv. I have no idea how you would discover other devices and set up a pairing, though.

---

### Post by ki4jgt on 2013-05-29
Sorry, wrong terminology. I meant was a pair required to send data. I'm working on a library and have already accomplish scanning by PIPING out the results of "hcitool scan." It creates a nice list of devices and their device names. This is it so far. I need to know if I can just send the data or if I also must pair the devices. Having only one bluetooth device, I cannot test it.

```

class tools():
	def scan(self):
		a = subprocess.Popen(["hcitool", "scan"], stdout = subprocess.PIPE).communicate()[0].split()[2:]
		if a == []:
			return "ERROR: Device appears to be turned off or not working. Try a device reset \"sudo hciconfig hci0 reset\""
		else:
			return a

	def send(self, mac, port, string):
		b = socket.socket(socket.AF_BLUETOOTH, socket.SOCK_STREAM, socket.BTPROTO_RFCOMM)
		b.connect((mac, port))
		b.send(bytes(string, "UTF-8"))
		b.close()

```

---

