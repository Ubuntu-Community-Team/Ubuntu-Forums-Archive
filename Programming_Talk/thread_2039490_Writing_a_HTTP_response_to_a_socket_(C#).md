---
title: "Writing a HTTP response to a socket (C#)"
date: 2012-08-09
forum: Programming Talk
---

### Post by dazman19 on 2012-08-09
So I ususally do all my coding in PHP/JS or Java. Now I have had to use C# to do a program on a windows machine and I have made a web server, which fires up some active x rubbish does its thing and returns a response. 

Since i had to write the whole web server I am wondering what i am doing wrong as the response back from the web server seems to be just plain text that I wrote to the socket, but i thought the HTTP headers would be interpereted differently by the browser. Firebug has this message:

The character encoding of the plain text document was not declared. The document will render with garbled text in some browser configurations if the document contains characters from outside the US-ASCII range. The character encoding of the file needs to be declared in the transfer protocol or file needs to use a byte order mark as an encoding signature.

Here is a snippet of what I have and my result:

```

//write it back to the socket
                            Byte[] bSendData = Encoding.ASCII.GetBytes(outputBuffer);
                            SendToBrowser(bSendData, ref mySocket);

//Which in turn calls this function:

 public void SendToBrowser(Byte[] bSendData, ref Socket mySocket)
        {
            int numBytes = 0; 
            try
            {
                if (mySocket.Connected)
                {
                    if ((numBytes = mySocket.Send(bSendData, bSendData.Length, 0)) == -1)
                    {
                        logServerMessage("Socket Error cannot Send Packet");
                    }
                    else
                    {
                        logServerMessage(String.Format("No. of bytes sent {0}", numBytes)); 
                    }
                }
                else
                {
                    logServerMessage("Connection Dropped....");
                }
            }
            catch (Exception e) 
            {
                logServerMessage(String.Format("Error Occurred : {0} ", e.Message)); 
            }
        }




 private string addHTTPHeader(string buffer)
        {
            string str = "";
            int contentLength = buffer.Length;
            str += "HTTP 1.1\r\n";
            str += "Server: eftpos-application\r\n";
            str += "Content-Type: text/html\r\n";
            str += "Accept-Ranges: bytes\r\n";
            str += "Content-Length: " + contentLength.ToString() + "\r\n\r\n";
            return str + buffer;
        }


```
And that makes a string that looks like this:

"
HTTP 1.1
Server: eftpos-application
Content-Type: text/html
Accept-Ranges: bytes
Content-Length: 105

Processing Transaction..... <script type="text/javascript">checkForEftposTransactionUpdate(120);</script>
"

What i dont understand is what am i missing from my HTTP header?

Do i have to write the Header to the socket, And then in a seperate write to the socket send the rest of the content?

As far as I am aware My header seems to comply enough with HTTP 1.1 if not i would be eager to know.

Any help is appreciated 

Cheers
D

---

### Post by dazman19 on 2012-08-11
Solved it. Was my http header. HTTP/1.1 was needed

---

