---
title: "Hex editing library for java?"
date: 2008-08-10
forum: Programming Talk
---

### Post by syko21 on 2008-08-10
I need a java library that will allow me to parse any type of file as a hex string. I've checked Sun's website through their api list and haven't found a suitable library for doing this. Does anyone know where else I can check? Any help at all is appreciated. Thanks.

---

### Post by NovaAesa on 2008-08-10
I'm not really sure if I understand what you are trying to do, but there is a way to convert from strings (eg "69A84B") to an actual number.

The Integer class has a static method called parseInt which takes a string argument and an integer argument. The string is the string that you want to convert from, and the integer is the radix you want to convert with (in this case you would set to 16). The method returns the value as an integer. Hope this helps =]

[quote="http://java.sun.com/javase/6/docs/api/"]
parseInt

public static int parseInt(String s,
                           int radix)
                    throws NumberFormatException

    Parses the string argument as a signed integer in the radix specified by the second argument. The characters in the string must all be digits of the specified radix (as determined by whether Character.digit(char, int) returns a nonnegative value), except that the first character may be an ASCII minus sign '-' ('\u002D') to indicate a negative value. The resulting integer value is returned.

    An exception of type NumberFormatException is thrown if any of the following situations occurs:

        * The first argument is null or is a string of length zero.
        * The radix is either smaller than Character.MIN_RADIX or larger than Character.MAX_RADIX.
        * Any character of the string is not a digit of the specified radix, except that the first character may be a minus sign '-' ('\u002D') provided that the string is longer than length 1.
        * The value represented by the string is not a value of type int. 

    Examples:

         parseInt("0", 10) returns 0
         parseInt("473", 10) returns 473
         parseInt("-0", 10) returns 0
         parseInt("-FF", 16) returns -255
         parseInt("1100110", 2) returns 102
         parseInt("2147483647", 10) returns 2147483647
         parseInt("-2147483648", 10) returns -2147483648
         parseInt("2147483648", 10) throws a NumberFormatException
         parseInt("99", 8) throws a NumberFormatException
         parseInt("Kona", 10) throws a NumberFormatException
         parseInt("Kona", 27) returns 411787
         

    Parameters:
        s - the String containing the integer representation to be parsed
        radix - the radix to be used while parsing s. 
    Returns:
        the integer represented by the string argument in the specified radix. 
    Throws:
        NumberFormatException - if the String does not contain a parsable int.[/quote]

---

### Post by syko21 on 2008-08-10
I wrote a small cryptography program back in High School when I was doing CS. The program was only designed to handle text files. I just got the urge to update it so that it can parse any type of file but to do that I would need to read the file in as a hex string. So the library I'm looking for is to help me read in any type of file so that I can encrypt the hex of that file and dump it into an encrypted format. Hope that explains what I want to do a little better. Thanks very much for the information though!

---

### Post by Reiger on 2008-08-10
Well there are bytestreams...
[PHP]
FileInputStream fis;
try {
  fis = new FileInputStream(myfile);
  int i=0;
  String s;
  while(i != -1) { /* -1 is a constant for 'EOF' : end of file. */
    i=fis.read();
    s=Integer.toString(i,16); /* convert to a 'number' String using the radix c.f. 16; but you may also want to use 26 for the characters in the Western alphabet. */
    /* ... insert code to process the String here... */
  }
  fis.close();
}
catch (Exception e) {
}
[/PHP]

---

### Post by HotCupOfJava on 2008-08-10
Well, java actually reads files as bytestreams, as the previous poster said. You may need to read the bytes, then convert to hex and pipe the output of THAT to the program you are trying to run......

---

### Post by syko21 on 2008-08-10
I will look into it further, that seems to be the best solution. The hex part was arbitrary I really just needed to be able to read any type of file into a workable format and I knew all files can be converted to hex.

---

### Post by tinny on 2008-08-10
You should use the apache commons codec lib.

[http://commons.apache.org/codec/](http://commons.apache.org/codec/)

[PHP]
//Encode as HEX
byte[] data = ....;
char[] hexChars = Hex.encodeHex(data);

//Decode HEX
data = Hex.decodeHex(hexChars);
[/PHP]

---

