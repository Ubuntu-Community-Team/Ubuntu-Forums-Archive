---
title: "really weird error in c++"
date: 2006-10-21
forum: Programming Talk
---

### Post by pontifex3 on 2006-10-21
hi, im trying to program the solitaire algorithm which is used in cryptonomicon if anyone has read it, the whole deck steps work fine but im having a strange problem with the getline command, at the beginning of the code, the program gives two options, wether the user wants to enter the card numbers diretly or if it wants the computer to auto-shuffle(generates random numbers, puts them in mod 54), independently after this step, i ask for the text to encrypt using getline(cin, text, '.'); so when the text has a . it should read it, the thing is that if the user chooses the computer to shuffle the deck it works just fine, but if you choose to enter your own values for the cards, i never reads the line, it looks like this:


Will you decrypt using an auto key? (y/n): n
Warning, cipher will be unencryptable if values are entered incorrectly
please enter all card values sepparated by spaces (top to bottom): 
28 20 3 31 53 46 30 54 8 9 43 29 38 45 19 14 5 10 41 37 52 47 15 24 21 36 22 26 39 32 7 12 50 42 27 40 33 49 1 2 16 17 34 13 35 4 48 11 23 25 51 6 44 18

Enter the text without spaces ending with " .  <return>": yzky.
.
.


and in using the key (which is just the seed for the srand, that i already found out doesn't work but doesnt matter for now)

Will you decrypt using an auto key? (y/n): y
Enter your key: 6
 
 The solitaire order goes as follows: 
17 43 31 27 15 14 16 13 24 29 19 45 7 50 36 39 2 46 26 1 40 47 35 48 41 4 21 28 34 30 53 11 12 8 52 20 44 9 38 37 54 5 42 49 23 3 6 32 33 25 10 22 18 51 
Enter the text without spaces ending with " .  <return>": hola.
i have read the value

PLAINTEXT: 


idtf


--------------------------------------------------------------------------
the code if as follows:

<div style="margin:20px; margin-top:5px">
	<div class="smallfont" style="margin-bottom:2px"><span class="highlight">Code</span>:</div>
	<pre class="ubuntu_codebackground" style="margin:0px; padding:6px; border:1px inset; width:640px; height:82px; overflow:auto"><div style="text-align:left;">
  if (op=='y')  //*****SHUFFLE AUTOMATICO DEL DECK COMIENZA******
    {
      for (i=1; i<=54; i++) deck[i]=0; //los valores deben ser 0 para poder comprobar si el lugar ya esta ocupado
      if (phase=='e')
	{
        cout << "\nAuto-shuffling started";
        cout << "\nWARNING: two auto-assigned keys will be the same if called during the same second";
        time (&sec);
        srand((unsigned)sec);
        cout << "\n\nYour auto-assigned key is: " << sec;
	} else
	  {
	    cout << "Enter your key: ";
	    cin >> sec;
	  }
    for (i=1; i<=54; i++)
      {
        found=false;
        while(!found)
          {
          sec = (rand()%54)+1; //genera posiciones de 1 a 54 y si esta vacio asigna el valor de las cartas en orden
          if (deck[sec]==0)
	    {
	    deck[sec]=i;
	    found=true;
	    }
	  }  //fin de asignacion
      }
    cout << " " << "\n The solitaire order goes as follows: " << endl;
    for (i=1; i<=54; i++)  //imprime el orden de las cartas
      {
	cout << deck[i] << " ";
      }
    }   //all of the upper part is the one that auto-shuffles and works fine
  else                      // si el usuario desea introducir sus propios valores del solitario
    {
      cout << "Warning, cipher will be unencryptable if values are entered incorrectly\n"
           << "please enter all card values sepparated by spaces (top to bottom): " << endl;
      for (i=1; i<=54; i++)  // lee las 54 cartas
	{
	  cin >> deck[i];
	}
    }
  cout << "\nEnter the text without spaces ending with \" .  <return>\": ";  //lectura del texto a encriptar
  getline(cin, text, '.');
  cout << "i have read the value";
df -h</div>

i've output the deck array after introducing it manually and it does save the values correctly and have also added cin.get(); cin.clear(); after reading the cards and it still wont read the text, any help appreciated, thanks for your help in advance!

---

### Post by pontifex3 on 2006-10-21
the code looks pretty bad in the post and i dont know how to place it the fancy way to here is the link to whole source

[http://fismat.umich.mx/~jjara/solitario.cpp](http://fismat.umich.mx/~jjara/solitario.cpp)

most comments are in spanish sorry about that, but the 5 lines that matter have two comments both in english :-D

---

### Post by public_void on 2006-10-22
I haven't been doing C++ for long but it looks like you want to use getline in <string>, however you haven't included it.

[IO getline]("http://www.cppreference.com/cppio/getline.html") and [string getline]("http://www.cppreference.com/cppstring/getline.html").

---

### Post by jlintz on 2006-10-22
use cin.flush() before your getline statement.  It will clear any characters in the input buffer so nothing leftover previously gets read in

---

