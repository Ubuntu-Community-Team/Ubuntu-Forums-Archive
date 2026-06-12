---
title: "Having trouble with VB"
date: 2011-01-16
forum: Programming Talk
---

### Post by Xeneth on 2011-01-16
Me and another are in class and have to program a simple server/client program.  I got the code, and have tried to run in using Mono-development.  The code runs great, but the connection not so much.


SERVER: 
```

Imports System.Net.Sockets
Imports System.Text
Module Module1
    Sub Main()
        Dim serverSocket As New TcpListener(8888)
        Dim clientSocket As TcpClient
        Dim counter As Integer

        serverSocket.Start()
        msg("Server Started")
        counter = 0
        While (True)
            counter += 1
            clientSocket = serverSocket.AcceptTcpClient()
            msg("Client No:" + Convert.ToString(counter) + " started!")
            Dim client As New handleClinet
            client.startClient(clientSocket, Convert.ToString(counter))
        End While

        clientSocket.Close()
        serverSocket.Stop()
        msg("exit")
        Console.ReadLine()
    End Sub

    Sub msg(ByVal mesg As String)
        mesg.Trim()
        Console.WriteLine(" >> " + mesg)
    End Sub

    Public Class handleClinet
        Dim clientSocket As TcpClient
        Dim clNo As String
        Public Sub startClient(ByVal inClientSocket As TcpClient, _
        ByVal clineNo As String)
            Me.clientSocket = inClientSocket
            Me.clNo = clineNo
Dim ctThread As Threading.Thread = New Threading.Thread(AddressOf doChat)
            ctThread.Start()
        End Sub
        Private Sub doChat()
            Dim requestCount As Integer
            Dim bytesFrom(10024) As Byte
            Dim dataFromClient As String
            Dim sendBytes As [Byte]()
            Dim serverResponse As String
            Dim rCount As String
            requestCount = 0

            While (True)
                Try
                    requestCount = requestCount + 1
                    Dim networkStream As NetworkStream = _
                            clientSocket.GetStream()
    networkStream.Read(bytesFrom, 0, CInt(clientSocket.ReceiveBufferSize))
    dataFromClient = System.Text.Encoding.ASCII.GetString(bytesFrom)
                    dataFromClient = _
                dataFromClient.Substring(0, dataFromClient.IndexOf("$"))
                    msg("From client-" + clNo + dataFromClient)
                    rCount = Convert.ToString(requestCount)
            serverResponse = "Server to clinet(" + clNo + ") " + rCount
                    sendBytes = Encoding.ASCII.GetBytes(serverResponse)
                    networkStream.Write(sendBytes, 0, sendBytes.Length)
                    networkStream.Flush()
                    msg(serverResponse)
                Catch ex As Exception
                    MsgBox(ex.ToString)
                End Try

            End While

        End Sub
    End Class
End Module

```


Client:
```

Imports System.Net.Sockets 
Imports System.Text 
Public Class xMainForm 
 
    Dim ipAdress As String 
    Dim clientSocket As New System.Net.Sockets.TcpClient() 
    Dim serverStream As NetworkStream 
 
 
 
    Private Sub xSubmitButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles xSubmitButton.Click 
        Dim serverStream As NetworkStream = clientSocket.GetStream() 
        Dim buffSize As Integer 
        Dim outStream As Byte() = _ 
        System.Text.Encoding.ASCII.GetBytes("Message from Client$") 
        serverStream.Write(outStream, 0, outStream.Length) 
        serverStream.Flush() 
        Dim inStream(10024) As Byte 
        buffSize = clientSocket.ReceiveBufferSize 
        serverStream.Read(inStream, 0, buffSize) 
        Dim returndata As String = _ 
        System.Text.Encoding.ASCII.GetString(inStream) 
        msg("Data from Server : " + returndata) 
    End Sub 
 
    Private Sub xMainForm_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load 
        msg("Client Started") 
        clientSocket.Connect("127.0.0.1", 8888) 
        xConnLabel.Text = "Client Socket Program - Server Connected" 
    End Sub 
 
    Sub msg(ByVal mesg As String) 
        xReturnLabel.Text = xReturnLabel.Text + Environment.NewLine + ">>  " + mesg 
    End Sub 
 
    Private Sub xExitButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles xExitButton.Click 
        Me.Close() 
 
    End Sub 
 
    Private Sub xClearButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles xClearButton.Click 
        xIPTextBox.Text = vbNullString 
        xPortTextBox.Text = vbNullString 
 
    End Sub 
End Class 

```


As stated, both code works by itself, but the server gets the error
"System.ArgumentOutOfRangeException:  Argument is out of range.
Parameter name: offset+size exceeds the size of the buffer
at System.Net.Sockets.NetworkStream.Read (System.Byte[] buffer, int32 offset, Int32 size) [0x00000]
at Server.Module1+handleClient.doChat() [0x00024] in ../Server.vb:57"

The thing is, it runs fine in Visual Studio on the other computer.

Any help here?

---

### Post by Xeneth on 2011-01-19
Not 100% why it didn't work, but I started a server from scratch and got it connected.  Just need to get threads working.  :)

---

