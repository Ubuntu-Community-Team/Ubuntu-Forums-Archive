---
title: "Monodevelop and  System.IO.Ports"
date: 2008-02-16
forum: Programming Talk
---

### Post by Tommy.86 on 2008-02-16
Hi, I have Mono 1.2.6 (Monodevelop 0.18 ) and I have a problem with namespace System.IO.Ports. I can only use System.IO, but i need System.IO.Ports for communication.

I found some instruction how solve that problem but  i don't understand it.

[http://www.ustash.com/mono/HowToSystemIOPorts.html](http://www.ustash.com/mono/HowToSystemIOPorts.html)

Can u help me? :(

---

### Post by JordanII on 2008-02-16
It appears to be saying this:

First open a terminal. Then type:

```
gedit SerialExample.cs
```

A text editor will pop up. Then paste this into it:
```

using System;
using System.IO.Ports;

public class SerialPortTest
{
	public static void Main(string[] args)
	{
		SerialPortTest myTest = new SerialPortTest();
		myTest.Test();
	}

	private SerialPort mySerial;

	// Constructor
	public SerialPortTest()
	{
	}

	public void Test()
	{
		if (mySerial != null)
			if (mySerial.IsOpen)

				mySerial.Close();

		mySerial = new SerialPort("/dev/ttyS0", 38400);
		

		mySerial.Open();


		mySerial.ReadTimeout = 400;

		SendData("ATI3\r");

		Console.WriteLine(ReadData()); // Should output some information about your modem firmware
	}

	public string ReadData()
	{
		byte tmpByte;
		string rxString = "";
			
		tmpByte = (byte) mySerial.ReadByte();

		while (tmpByte != 255)
		{
			rxString += ((char) tmpByte);
		
			tmpByte = (byte) mySerial.ReadByte();			
		}
	
		return rxString;
	}

	public bool SendData(string Data)
	{
		// To send a string, we need to first convert to a character array
		char[] charData = Data.ToCharArray();

		// Then convert to a byte array
		byte[] byteData = new byte[charData.Length];
		for (int cnt = 0; cnt < byteData.Length; cnt++)
			byteData[cnt] = (byte) charData[cnt];

		// We send the serial data
		mySerial.Write(byteData, 0, byteData.Length);

		return true;		
	}
}
```

Save the file and exit the text editor. Then go back to the terminal and type: 
```

gmcs SerialExample.cs
```

Then:

```
mono SerialExample.exe
```

You should then get output similar to this:

```
clint@home:~/Projects/SerialPortExample$ mono SerialExample.exe 

Sportster 14,400/FAX RS Rev. 1.5

OK

```

I've never tried this so I can't guarantee it will work... I'm just decoding the tutorial (or trying to.) I hope it works. :)

---

### Post by Tommy.86 on 2008-02-16
It doesn't work. :(

```

Unhandled Exception: System.IO.IOException: I/O Error
  at System.IO.Ports.SerialPortStream..ctor (System.String portName, Int32 baudRate, Int32 dataBits, Parity parity, StopBits stopBits, Boolean dtrEnable, Boolean rtsEnable, Handshake handshake, Int32 readTimeout, Int32 writeTimeout, Int32 readBufferSize, Int32 writeBufferSize) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.Ports.SerialPortStream:.ctor (string,int,int,System.IO.Ports.Parity,System.IO.Ports.StopBits,bool,bool,System.IO.Ports.Handshake,int,int,int,int)
  at System.IO.Ports.SerialPort.Open () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.Ports.SerialPort:Open ()
  at SerialPortTest.Test () [0x00000] 
  at SerialPortTest.Main (System.String[] args) [0x00000]
```

---

### Post by JordanII on 2008-02-16
> **Tommy.86 said:**
> It doesn't work. :(

```

Unhandled Exception: System.IO.IOException: I/O Error
  at System.IO.Ports.SerialPortStream..ctor (System.String portName, Int32 baudRate, Int32 dataBits, Parity parity, StopBits stopBits, Boolean dtrEnable, Boolean rtsEnable, Handshake handshake, Int32 readTimeout, Int32 writeTimeout, Int32 readBufferSize, Int32 writeBufferSize) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.Ports.SerialPortStream:.ctor (string,int,int,System.IO.Ports.Parity,System.IO.Ports.StopBits,bool,bool,System.IO.Ports.Handshake,int,int,int,int)
  at System.IO.Ports.SerialPort.Open () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.Ports.SerialPort:Open ()
  at SerialPortTest.Test () [0x00000] 
  at SerialPortTest.Main (System.String[] args) [0x00000]
```

Hmm... then I'm afraid i can't help... sorry.

---

### Post by Tommy.86 on 2008-02-17
My project was in runtime version NET 1.1, and if i want to use System.IO.Ports, i have to set version NET 2.0 :)

problem with Syste.IO.Ports solved :)

---

### Post by ghidalgo on 2008-05-04
Hola 

 Por primera vez estoy utilizando monodevelop, anteriormente he realizado aplicaciones en sharpdevelop(windows), sin embargo es de mi interez comenzar
a trabajar en linux. Me he encontrado con el mismo problema que comentan ya que la clase System.IO.Ports no aparece en Monodevelop que baje con sinaptic.
 En el comentario anterior de esta discusion lo solucionan actualizando a .net2.0 esto quiere decir actualizar la maquina virtual, la cual no he encontrado para ubuntu. Espero pueda alguien guiarme.

gracias.

---

### Post by ghidalgo on 2008-05-04
I'm sorry i forgot writing in english.

I started using monodevelop and i have the same problem.
How can i update the .net virtual machine in ubuntu?

thanks.

---

