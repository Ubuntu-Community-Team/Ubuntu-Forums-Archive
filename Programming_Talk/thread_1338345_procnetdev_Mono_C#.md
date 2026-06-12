---
title: "/proc/net/dev Mono C#"
date: 2009-11-26
forum: Programming Talk
---

### Post by venomenus on 2009-11-26
Hi,

I am currently writing an application that monitors network speed/data in Mono using C#, I am able to read the adapter and received bytes fine but am struggling to find a logical way of reading the transmit bytes as depending on how much data has been downloaded/uploaded this keeps moving and white spaces keep changing.

Am I overlooking something really simple here?, the only way I can think of currently doing this is checking how many characters are in my received bytes every time I poll this data and changing the sub string position for getting the sent bytes, but that just doesn't seem like the way it should be done.

this is in the "proc/net/dev" file btw.

Any help/advice would be much appreciated :D

Thanks in advance.

---

### Post by phrostbyte on 2009-11-26
Can you provide a code block which shows what you are doing?

---

### Post by venomenus on 2009-11-26
This is a dirty theoretical example of getting the sent bytes with  the problem of the moving white spaces (depending on the other values in that line), I cant seem to see any other way of extracting the send bytes.

```

private void refreshTimer_Tick(object sender,EventArgs e)
		{
			while(!sr.EndOfStream)
			{
				string line = sr.ReadLine();
				if(line.StartsWith("  eth0"))
				{
					string[] splitter = line.Split(new char[]{' '});
					string[] recsplitter = splitter[2].Split(new char[]{':'});
					
					//Recieved Bytes
					double recieved = Convert.ToDouble((long.Parse(recsplitter[1])));					
					lblDownData.Text = GetFileSize(recieved);
					
					if(lastRecieved > 0)
						lblDownSpeed.Text = GetFileSize(recieved - lastRecieved);						
					else
						lblDownSpeed.Text = GetFileSize(0);
						
					lastRecieved = recieved;
					
					//Sent Bytes
					
					//Will fail here as the white spaces will move
					double sent = Convert.ToDouble((long.Parse(splitter[41])));
					lblUpData.Text = GetFileSize(sent);
					
					if(lastSent > 0)
						lblUpSpeed.Text = GetFileSize(sent - lastSent);						
					else
						lblUpSpeed.Text = GetFileSize(0);
					
					lastSent = sent;
					
					break;
				}
			}
			
			sr.BaseStream.Flush();
			sr.BaseStream.Position = 0;
		}

```

Thanks

---

### Post by phrostbyte on 2009-11-27
You might need to delimit by the TAB character.

System.Windows.Forms.Keys.Tab returns the TAB character, which has the ASCII code of 9

'\t' might also work.

---

### Post by venomenus on 2009-11-27
> **phrostbyte said:**
> You might need to delimit by the TAB character.

System.Windows.Forms.Keys.Tab returns the TAB character, which has the ASCII code of 9

'\t' might also work.

Hi thanks for the advice but there are not tabs in this file. :(
There just seems to be no logical structure to it. Which is odd as I'm under the impression that the reason for the Proc file system is for data to be read and interacted with. :cry:

---

### Post by unruledboy on 2013-03-02
Hi,

   I just started learning development for Ubuntu. I am trying to read info from /proc/stat using Mono C#. But when I use FileInfo, I get 0 as Length, and I use StreamReader I got empty string. How do you manage to open the file and read the data?

---

### Post by unruledboy on 2013-03-02
I finally figured it. It's all my fault. Because file like /proc/stat in the proc virtual file system is not really a real file. It's normal for the length to be zero.


All I need to do is to use StreamReader to read the file content, either line by line (ReadLine) or the whole (ReadToEnd)

---

