---
title: "VB.NET to C++ (Linux) code conversion"
date: 2011-06-29
forum: Programming Talk
---

### Post by brianinoshkosh on 2011-06-29
im having a small problem. i writing a program registration system for a vb.net app. it works great but i also need to generate the same codes on the web aswell. 2 of the functions im using are a bit confusing to me. could anyone help me out on porting these 2 functions into php or even a linux executable i could call from a php script.
 
here are the two functions.
 
```

Private Function TripleDESEncode(ByVal value As String, ByVal key As String) As String
        Dim des As New Security.Cryptography.TripleDESCryptoServiceProvider
        des.IV = New Byte(7) {}
        Dim tiv() As Byte = New Byte(-1) {}
        Dim pdb As New Security.Cryptography.PasswordDeriveBytes(key, tiv)
        des.Key = pdb.CryptDeriveKey("RC2", "MD5", 128, New Byte(7) {})
        Dim ms As New IO.MemoryStream((value.Length * 2) - 1)
        Dim encStream As New Security.Cryptography.CryptoStream(ms, des.CreateEncryptor(), Security.Cryptography.CryptoStreamMode.Write)
        Dim plainBytes As Byte() = Encoding.UTF8.GetBytes(value)
        encStream.Write(plainBytes, 0, plainBytes.Length)
        encStream.FlushFinalBlock()
        Dim encryptedBytes(CInt(ms.Length - 1)) As Byte
        ms.Position = 0
        ms.Read(encryptedBytes, 0, CInt(ms.Length))
        encStream.Close()
        des = Nothing
        pdb = Nothing
        ms = Nothing
        encStream = Nothing
        plainBytes = Nothing
        Return Convert.ToBase64String(encryptedBytes)
        encryptedBytes = Nothing
    End Function
    Private Function TripleDESDecode(ByVal value As String, ByVal key As String) As String
        Dim des As New Security.Cryptography.TripleDESCryptoServiceProvider
        des.IV = New Byte(7) {}
        Dim pdb As New Security.Cryptography.PasswordDeriveBytes(key, New Byte(-1) {})
        des.Key = pdb.CryptDeriveKey("RC2", "MD5", 128, New Byte(7) {})
        Dim encryptedBytes As Byte() = Convert.FromBase64String(value)
        Dim ms As New IO.MemoryStream(value.Length)
        Dim decStream As New Security.Cryptography.CryptoStream(ms, des.CreateDecryptor(), Security.Cryptography.CryptoStreamMode.Write)
        decStream.Write(encryptedBytes, 0, encryptedBytes.Length)
        decStream.FlushFinalBlock()
        Dim plainBytes(CInt(ms.Length - 1)) As Byte
        ms.Position = 0
        ms.Read(plainBytes, 0, CInt(ms.Length))
        decStream.Close()
        des = Nothing
        pdb = Nothing
        ms = Nothing
        decStream = Nothing
        Return Encoding.UTF8.GetString(plainBytes)
        plainBytes = Nothing
    End Function

```

---

### Post by megabytemonster on 2011-06-30
You should be able to run VB.NET code in Linux, I do so myself on a webserver. You need to install Mono (Linux version of .NET Framework).[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

---

