---
title: "Java File IO"
date: 2011-10-19
forum: Programming Talk
---

### Post by DarkAmbient on 2011-10-19
In C I would just use fopen("filepath", mode) to open a text/binary -file to read/write/append from/to.

In Java, RandomAccessFile seems like a good equivalent, but if I understood it right, it is only for binary-files(?). And other file-handlers seems to need one instance for reading, and one instance for writing.

So, my question is. In Java how do I do something similar to fopen?

---

### Post by PaulM1985 on 2011-10-19
I think you want Scanner for reading ([http://download.oracle.com/javase/1,5.0/docs/api/java/util/Scanner.html](http://download.oracle.com/javase/1,5.0/docs/api/java/util/Scanner.html)) and FileWriter for writing ([http://download.oracle.com/javase/1,5.0/docs/api/java/io/FileWriter.html](http://download.oracle.com/javase/1,5.0/docs/api/java/io/FileWriter.html))

You need to have two objects, one for reading and one for writing.

Paul

---

### Post by DarkAmbient on 2011-10-19
I'm gonna read up some more on this, right now I'm a tad confused 'bout t'is. Thanks for the respond and the links.

---

### Post by veroslav on 2011-10-21
For reading of the text files, use a FileReader wrapped by a BufferedReader, like this:

```
BufferedReader br = new BufferedReader(new FileReader("file.txt"));
```For reading of the binary files, use a FileInputStream wrapped by a BufferedInputStream, like this:

```
BufferedInputStream is = new BufferedInputStream(new FileInputStream("file.bin"));
```RandomAccessFile is not used that often, but when used on binary files, it enables to write and read from any place in the file.

Finally, you will have to create separate streams for writing and reading respectively.

Kind Regards,
Veroslav

---

### Post by Some Penguin on 2011-10-21
When using Readers that convert from bytes to Character, you really should specify the file encoding rather than letting the JVM use the system default.

---

### Post by DarkAmbient on 2011-10-22
Man do I feel good that you guys recommended FileReader/Write and BufferedReader/Writer. That's exacly what I went for when trying my way forth. Been coding like some crazy dude the last days. So far I've created few classes, one for filehandling, one for retrieving values after keys from "configfiles" and some other.. Some stuff is probably not sufficient, or implemented in a ugly way. But this is what I've come up with. Feel free being critical if your up for it. Sorry for the lenght of it.

Main class... to show some stuff File, Config can do.

```

package <censured>;

import <censured>.io.Config;
import <censured>.io.File.e_mode;
import <censured>.io.File.e_type;

import java.io.IOException;


/**
 *
 * @author Rikard Johansson
 */
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) throws IOException {

        if(lava.Platform.getOsGenre()==lava.Platform.UNIX) {
            System.out.print("Unix-platform\n");
        }

        Config tr=new Config("file.text");

        System.out.printf("this is a int: %d\n", tr.get_int("aint"));
        System.out.printf("this is a bool: %b\n", tr.get_boolean("abool"));
        System.out.printf("this is a string: %s\n", tr.get_string("astring"));
        System.out.printf("this is a float: %.20f\n", tr.get_float("afloat"));

        tr.close();

        Config bw=new Config();
        
        if(bw.open("file.binary", e_type.BINARY, e_mode.WRITENEW)) {

            bw.write("Hello this is a %d text\n");
            bw.write(1337);
            bw.close();
            
            Config br=new Config();

            if(br.open("file.binary", e_type.BINARY, e_mode.READ)) {

                int[]i=new int[1];

                // since 1 char is 2 byte. and file contains string and 1 int
                // read (filesize - size of int)/2
                String in=br.read(0, ((int)br.get_filesize()-(Integer.SIZE/Byte.SIZE))/2);
                
                if(br.read(i)) {
                    System.out.print(String.format(in, i[0]));
                }
            }
        }
    }
}

```

Main.java need this pasted beneath in a textfile in the same folder as the Main.java, for the "test" to work.

```
abool: 			True
aint:	-435
afloat:	1.054030f
astring: 	this is a string
intarr:	1,23, 3,  344 , 3463
```


Class File, lots of read & write method, so you can throw all kind of datatypes at 'em. 

```
/*
 *   ffFFFFFFFF iIIIi lLLLl      EEEEEEEE
 *    fFFFFFFFF  III   LLL       EEEEEEEE
 *     FFF       III   LLL       EEE  e
 *     FFFff     III   LLL       EEEee
 *     FFF       III   LLL   ll  EEE  e
 *     FFF       III   LLLLLLLL  EEEEEEEE
 *    fFFFf     iIIIi lLLLLLLLL  EEEEEEEE
 */

package <censured>.io;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;

import java.io.IOException;

/**
 *
 * @author Rikard Johansson <censured>@gmail.com>
 */
public class File {

    public enum e_mode { NONE,
                         READ,
                         APPEND,
                         WRITENEW };

    public enum e_type { NONE,
                         TEXT,
                         BINARY };

    String m_filename;
    private boolean m_set;
    private java.io.File m_file;

    private e_mode m_mode;
    private e_type m_type;
    
    private BufferedReader m_text_in;   // textual read
    private BufferedWriter m_text_out;  // textual write

    private DataInputStream m_bin_in;   // binary read
    private DataOutputStream m_bin_out; // binary write


    public File() {
        m_file=null;
        m_set=false;
        m_mode=m_mode.NONE; m_type=m_type.NONE;
    }

    /**
     * Constructor, opens file after "name"
     *
     * @param name
     * @throws IOException
     */
    public File(String name) throws IOException {
        this();
        open(name, e_type.TEXT, e_mode.READ);
    }

    /**
     * Opens a "file" in text or binary -mode for reading or writing.
     *
     * @param name
     * @param type
     * @param mode
     * @return boolean after success
     * @throws IOException
     */
    public final boolean open(String name, e_type type, e_mode mode) throws IOException  {

        if(m_file!=null)
            close(); // If some other file is open, close it


        this.m_filename = name;
        this.m_file=new java.io.File(name);
        this.m_mode=mode;
        this.m_type=type;

        DataInputStream  dis=null;
        DataOutputStream dos=null;

        switch (m_mode) {

            case READ: {
                dis=new DataInputStream(new FileInputStream(m_file));
                break;
            }
            case WRITENEW: {
                dos=new DataOutputStream(new FileOutputStream(m_file));
                break;
            }
            case APPEND: {
                dos=new DataOutputStream(new FileOutputStream(m_file, true));
                break;
            }

            default: {
                throw new IOException("no mode set in open file");
            }

        }

        if(binary_file()) {

            if(mode_read())
                this.m_bin_in=dis;
            else
                this.m_bin_out=dos;
            
        } else {

            if(mode_read()) {
                this.m_text_in=new BufferedReader(new InputStreamReader(dis));
                this.mark(); // mark beginning
            }
            else
                m_text_out=new BufferedWriter(new OutputStreamWriter(dos));
        }
        
	return true;
    }


    /**
     * finish off all objects
     * @throws IOException
     */
    public void close() throws IOException {

        System.out.println("closing files");

        this.m_text_in.close();
        this.m_text_out.close();
        this.m_bin_in.close();
        this.m_bin_out.close();
        this.m_filename=null;
        this.m_file=null;
    }

    
    public boolean is_open() {
        return (this.m_file!=null ? true : false);
    }

    private boolean text_file() {
        return (this.m_type==e_type.TEXT ? true : false);
    }

    private boolean binary_file() {
        return (this.m_type==e_type.BINARY ? true : false);
    }

    private boolean mode_read() {
        return this.m_mode==m_mode.READ ? true:false;
    }

    private boolean mode_append() {
        return this.m_mode==m_mode.APPEND ? true:false;
    }

    private boolean mode_write() {
        return this.m_mode==m_mode.WRITENEW ? true:false;
    }

    public String get_filename() {
        return this.m_filename;
    }

    /**
     * @return filesize in bytes
     */
    public long get_filesize() {

        assert(m_file!=null);
        
        return this.m_file.length();
    }

    /**
     * mark the readerhead position
     * sets m_set to true, which indicate that the we are at start of file
     * @throws IOException
     */
    protected void mark() throws IOException {
        m_text_in.mark((int)get_filesize());
        this.m_set=true;
    }

    /**
     * reset readerhead to marked position
     * @throws IOException
     */
    protected void reset() throws IOException {
        m_text_in.reset();
        this.m_set=true;
    }


    /**
     * write a String to a binary or text -file
     * if binary, 2 byte a character
     * if text, 1 byte on ascii, 2 byte on unicode.. i guess?
     * @param text
     * @throws IOException
     */
    public void write(String text) throws IOException {
        
        assert(m_file!=null);

        if(mode_write() || mode_append()) {
            
            if(binary_file())
                m_bin_out.writeChars(text);
            else {
                m_text_out.write(text);
                m_text_out.flush();
            }
        } else {
            throw new IOException("File "+m_filename+" write (String) exception, file is readonly\n");
        }
    }

    /**
     * write a bool to a binaryfile (1 byte)
     * @param bool
     * @throws IOException
     */
    public void write(boolean bool) throws IOException {
        assert(m_file!=null);

        if(this.binary_file() && (mode_write() || mode_append())) {
                m_bin_out.writeBoolean(bool);
                m_bin_out.flush();
        } else {
            throw new IOException("File "+m_filename+": write(bool) exception\n");
        }
    }


    /**
     * write a byte to a binaryfile
     * @param b
     * @throws IOException
     */
    public void write(byte b) throws IOException {
        assert(m_file!=null);

        if(this.binary_file() && (mode_write() || mode_append())) {
                m_bin_out.writeByte(b);
                m_bin_out.flush();
        } else {
            throw new IOException("File "+m_filename+" write (byte) exception\n");
        }
    }


    /**
     * write a short to a binaryfile (2 byte)
     * @param s
     * @throws IOException
     */
    public void write(short s) throws IOException {
        assert(m_file!=null);

        if(this.binary_file() && (mode_write() || mode_append())) {
                m_bin_out.writeShort(s);
                m_bin_out.flush();
        } else {
            throw new IOException("File "+m_filename+" write (short) exception\n");
        }
    }

    /**
     * write a int to a binaryfile (4 byte)
     * @param i
     * @throws IOException
     */
    public void write(int i) throws IOException {
        assert(m_file!=null);

        if(this.binary_file() && (mode_write() || mode_append())) {
                m_bin_out.writeInt(i);
                m_bin_out.flush();
        } else {
            throw new IOException("File "+m_filename+" write (int) exception\n");
        }
    } 

    /**
     * write a float to a binaryfile (4 byte)
     * @param f
     * @throws IOException
     */
    public void write(float f) throws IOException {
        assert(m_file!=null);

        if(this.binary_file() && (mode_write() || mode_append())) {
                m_bin_out.writeFloat(f);
                m_bin_out.flush();
        } else {
            throw new IOException("File "+m_filename+": write(float) exception\n");
        }
    }

    /**
     * write a bytearray to a binaryfile (a byte a index)
     * @param array
     * @throws IOException
     */
    public void write(byte[]array) throws IOException {
        assert(m_file!=null);

        if(this.binary_file() && (mode_write() || mode_append())) {
                m_bin_out.write(array);
                m_bin_out.flush();
 
        } else {
            throw new IOException("File "+m_filename+": write(byte[]array) exception\n");
        }
    }

    /**
     * write a shortarray to a binaryfile (2 byte a index)
     * @param array
     * @throws IOException
     */
    public void write(short[]array) throws IOException {
        assert(m_file!=null);

        if(this.binary_file() && (mode_write() || mode_append())) {
            for(int i=0; i<array.length; i++) {
                m_bin_out.writeShort(array[i]);
                m_bin_out.flush();
            }
        } else {
            throw new IOException("File "+m_filename+" write (short[]array) exception\n");
        }
    }

    /**
     * write a intarray to a binaryfile (4 byte a index)
     * @param array
     * @throws IOException
     */
    public void write(int[]array) throws IOException {

        assert(m_file!=null);

        if(this.binary_file() && (mode_write() || mode_append())) {
            for(int i=0; i<array.length; i++) {
                m_bin_out.writeInt(array[i]);
                m_bin_out.flush();
            }
        } else {
            throw new IOException("File "+m_filename+" write (int[]array) exception\n");
        }
    }

    /**
     * write a floatarray to a binaryfile
     * @param array
     * @throws IOException
     */
    public void write(float[]array) throws IOException {

        assert(m_file!=null);

        if(this.binary_file() && (mode_write() || mode_append())) {
            for(int i=0; i<array.length; i++) {
                m_bin_out.writeFloat(array[i]);
                m_bin_out.flush();
            }
        } else if(mode_write() || mode_append()) {
            System.out.println("Error: trying to write a float-array to a textfile");
        } else {
            throw new IOException("File "+m_filename+" write (float[]array) exception\n");
        }
    }

    /**
     * write a chararray to a binaryfile
     * @param array
     * @return boolean after outcome
     * @throws IOException
     */
    public boolean read(char[]array) throws IOException {

        assert(m_file!=null);

        if(this.binary_file()) {
            for(int i=0;i<array.length; i++) {
                array[i]=m_bin_in.readChar();
            }
        } else {
            System.out.println("Error: attempting to read a char from a textfile");
            return false;
        }
        return true;
        
    }

    /**
     * read a bytearray from a binaryfile
     * @param array
     * @return boolean after outcome
     * @throws IOException
     */
    public boolean read(byte[]array) throws IOException {

        assert(m_file!=null);

        if(this.binary_file()) {
            
            for(int i=0;i<array.length; i++) {
                array[i]=(byte)m_bin_in.read();
            }
        } else {

            System.out.println("Error: attempting to read a byte from a textfile");
            return false;
        }
        return true;
    }

    /**
     * read a shortarray from a binaryfile
     * @param array
     * @return boolean after outcome
     * @throws IOException
     */
    public boolean read(short[]array) throws IOException {

        assert(m_file!=null);

        if(this.binary_file()) {

            for(int i=0;i<array.length; i++) {
                array[i]=m_bin_in.readShort();
            }
        } else {
            System.out.println("Error: attempting to read a short from a textfile");
            return false;
        }

        return true;
    }

    /**
     * read a intarray from a binaryfile
     * @param array
     * @return boolean after outcome
     * @throws IOException
     */
    public boolean read(int[]array) throws IOException {

        assert(m_file!=null);

        if(this.binary_file()) {

            for(int i=0;i<array.length; i++) {
                array[i]=m_bin_in.readInt();
            }
        } else {
            System.out.println("Error: attempting to read a int from a textfile");
            return false;
        }
        return true;
    }

    /**
     * read floatarray from a binaryfile
     * @param array
     * @return
     * @throws IOException
     */
    public boolean read(float[]array) throws IOException {
        
        assert(m_file!=null);

        if(this.binary_file()) {

            for(int i=0;i<array.length; i++) {
                array[i]=m_bin_in.readFloat();
            }
        } else {
            System.out.println("Error: attempting to read a float from a textfile");
            return false;
        }
        return true;
    }

    /**
     * Read bytes from a binary- or text -file.
     * Starting at @param offset, read value of @param len bytes
     * @param offset
     * @param len
     * @return String
     */
    public String read(int offset, int len) throws IOException {

        assert(m_file!=null);

        /** check so we dont exceed filesize */
        if((offset+len) > this.get_filesize()) {
            throw new IOException("bytereading out of bound\n");
        }

        String ret_str=null;
        char[]charbuffer=new char[len];

        if(!binary_file()) {

            if(!m_set)
                reset(); // reset readerhead

            // for some reason I get IOError calling read(...) with offset as second arg
            // solved it by using skip instead...
            m_text_in.skip(offset);

            if((m_text_in.read(charbuffer, 0, len)) != -1) {
                ret_str = new String(charbuffer);
            } else {
                System.out.println("error reading file");
            }
        }
        else {

            m_bin_in.skip(offset);

            for(int i=0;i<len;i++)
                charbuffer[i]=m_bin_in.readChar();

            ret_str=new String(charbuffer);
        }

        return ret_str;
    }
}
```

Config reads values of key-names thrown at it. 

```

/*
 *   CCCCC    OOOOOO    NNN  NNNn   ffFFFFFFFF iIIIi   GGGGGG
 *  CCCCCCC  OOOOOOOO   NNNn NNN   fffFFFFFFFF  III   GGGGGGGG
 * CCC   CC OOOo  oOOO  NNNN NNN  f/  FFF       III   GGG   GG
 * CC       OOO    OOO  NNNNNNNN  f   FFFFF     III   GGG
 * CC       OOO    OOO  NNNNNNNN      FFFFf     III   GGG GG
 * CCC   CC OOOo  oOOO  NNN NNNN      FFF       III   GGG  GGG
 *  CCCCCCC  OOOOOOOO   NNN nNNN      FFF       III   GGGGGGGG
 *   CCCCC    OOOOOO  nnNNN  NNN     fFFFf     iIIIi   GGGGGG
 */

package <censured>.io;

import <censured>.util.StringParser;
import java.io.IOException;
import java.util.HashMap;
import java.util.Map;

/**
 *
 * @author Rikard Johansson <censured@gmail.com>
 *
 * Class that reads configfiles
 */
public class Config extends File {

    private Map<String,String>m_buffer;

    /**
     * init configclass
     */
    public Config() {
        m_buffer=new HashMap<String, String>();
    }

    /**
     * init configclass, opens a file in textual readmode
     * @param name
     * @throws IOException
     */
    public Config(String name) throws IOException {
        this();
        this.open(name);
    }

    @Override
    public void close() {
        m_buffer.clear();
    }

    /**
     * opens a file in textual readmode
     * @parameter name
     * @throws IOException
     */
    private void open(String name) throws IOException {
        
        if(!this.open(name, e_type.TEXT, e_mode.READ)) {
            System.out.println("Config->Open: Unable to open file");
            return;
        }
        
        /*
         * read file, split to array on new line
         */
        String[]line=(this.read(0, (int)this.get_filesize())).split("\n");

        /*
         * loop through lines
         */
        for(int i=0; i<line.length; i++) {

            // remove spaces and tabs from the beginning of the line
            while(line[i].startsWith(" ") || line[i].startsWith("\t"))
                line[i]=line[i].substring(1);

            if (line[i].charAt(0) != '#') { // ignored line upon this

                String key=null;
                String value=null;

                key=line[i].substring(0, line[i].indexOf(":"));

                value=line[i].substring(line[i].indexOf(":") + 1);

                if(value.contains("#")) {
                    value=value.substring(0, value.indexOf("#"));
                }

                int beg=0;
                int end=value.length();

                while(value.substring(beg).startsWith(" ") || value.substring(beg).startsWith("\t"))
                    beg++;

                while(value.substring(beg, end).endsWith(" ") || value.substring(beg, end).endsWith("\t"))
                    end--;

                // it's a keeper
                m_buffer.put(key, value.substring(beg, end));

            } else {
                System.out.println("ignoring");
            }
	}
    }

    public int get_int(String param) {
        return Integer.parseInt(get_string(param));
    }


    public float get_float(String param) {
        return Float.parseFloat(get_string(param));
    }


    public boolean get_boolean(String param) {
        return Boolean.parseBoolean(get_string(param));
    }


    public String get_string(String param) {

        String result=null;

        if((result=m_buffer.get(param))==null) {
            System.out.printf("Error, unable to find key %s in %s\n", param, get_filename());
        }

        if(result==null || result.equals("")) {
            System.out.printf("headsup: fetched value of %s is empty, therefor set to void\n", param);
            result="void";
        }

        return result;
    }

    /**
     * 
     * @param param
     * @return param converted to int[]array
     */
    public int[] get_int_array(String param) {
        
        int[]array=null;
        int indexes=0;

        // check if String value "has a value"
        if (get_string(param).length()>0) {

            // remove all space, tabs characters
            String buf=get_string(param).replaceAll("\\s", "");
            
            if(buf.endsWith(","))
                buf=buf.substring(0, buf.length()-1);

            /*
             * only pass strings with an endless range of 1-9 number
             * long numeric values with a colon squished in between
             */
            if (buf.matches("\\d{1,9}(?:[,]\\d{1,9})*$")) {

                // this is a valid array, parse
                StringParser parse = new StringParser(buf,',');

                array=new int[parse.get_count()];

                if(array.length>0) {
                    for(int i=0 ; i < array.length ; i++) {
                            array[i]=Integer.parseInt(parse.index(i));
                    }
                }
                else {
                //  log_error("CConfig->get_int_array: to few values for param \"%s\"", param);
                    System.out.printf("to few values\n");
                }
            }
            else {
                System.out.printf("param does not seems to be valid, either contains letter or containts a 9+ digit number\n");
//			log_error("Config->get_int_array: param \"%s\" does not seem to be an int array", param);
            }
	}
	else {
            System.out.printf("to few character\n");
//		log_error("Config->get_int_array: invalid param \"%s\", to few characters", param);
	}

	return array;
    }
      // will add this...
//    public boolean get_int_vector(String param, Vector<int>v) {
//        return true;
//    }
}

```

This class is kinda overkill as of now, but I'm planning to make it more useful.
```

/*
 *   SSSSS    TTTTTTTTTTTT rRRRRRR   iIIIi  NNN  NNNn GGGGGGGg  pPPPPPp
 *  SSSSSSSS  TTTTTTTTTTTT RRRRRRRR   III   NNNn NNN  GGGGGGGgg PPPPPPPP
 *  SSS     s     tTTt     RRR  RRR   III   NNNN NNN  GGG     g PPP  PPP
 *  SSSSSSSs       TT      RRR  RRr   III   NNNNNNNN  GGG gg    PPPPPPP
 * s     SSS       TT      RRRRRR     III   NNN NNNN  GGG  GGg  PPP
 *  SSSSSSSS      tTTt     RRR  RRr   III   NNN nNNN  GGGGGGGG  PPP
 *    SSSSS      tTTTTt    RRR  RRRr iIIIi nNNN  NNN  GGGGGGGG pPPPp   .....
 *                                                          g
 */

package <censured>.util;

/**
 *
 * @author Rikard Johansson <censured@gmail.com>
 */
public final class StringParser {

    private String[]m_sub_str;
    private int m_count;

    /**
     * 
     * @param string
     * @param delimiter
     */
    public StringParser(String string, char delimiter) {
        parse(string, String.valueOf(delimiter));
    }

    /**
     *
     * @param string
     * @param delimiter
     */
    public void parse(String string, String delimiter) {
        m_sub_str=string.split(delimiter);
    }

    /**
     * 
     * @return length of parsed array
     */
    public int get_count() {
        return m_sub_str.length;
    }

    /**
     * 
     * @param index
     * @return index-value of int array as String
     */
    public String index(int index) {
        return m_sub_str[index];
    }
}
```

---

### Post by ofnuts on 2011-10-22
> **DarkAmbient said:**
> So far I've created few classes, one for filehandling, one for retrieving values after keys from "configfiles"Reinventing **java.util.Properties** ?

---

### Post by DarkAmbient on 2011-10-23
> **Some Penguin said:**
> When using Readers that convert from bytes to Character, you really should specify the file encoding rather than letting the JVM use the system default.

Thank you for the heads'up. Will duckduckgo on it right away. :)


> **ofnuts said:**
> Reinventing **java.util.Properties** ?


They aren't to similar I hope? :-S My Config goes through textfile on open. Stores every String matching "something:" as keys. And the rest of the (trimmed) line as value. (or until # is found which is a commentmark). Guess the part where you fetch value by key is the similar part?

---

### Post by ofnuts on 2011-10-23
> **DarkAmbient said:**
> They aren't to similar I hope? :-S My Config goes through textfile on open. Stores every String matching "something:" as keys. And the rest of the (trimmed) line as value. (or until # is found which is a commentmark). Guess the part where you fetch value by key is the similar part?Pretty close. See [http://en.wikipedia.org/wiki/.properties](http://en.wikipedia.org/wiki/.properties)

If you intend to make your code public, better stick with the de facto standard. For more complex configuration stuff, you can use XML (there are XML parsers for Java, so it's quite painless)

---

### Post by DarkAmbient on 2011-10-23
> **ofnuts said:**
> Pretty close. See [http://en.wikipedia.org/wiki/.properties](http://en.wikipedia.org/wiki/.properties)

If you intend to make your code public, better stick with the de facto standard. For more complex configuration stuff, you can use XML (there are XML parsers for Java, so it's quite painless)

Don't mind sharing what I've written so far. (But only as an example of what not to do. *harrharr*). Also, added a log-system to my project now if anyone is interested. :)

And alas, that was kinda the same deal. Except my class is quite simple. Well, thanks for enlighten me. Java seems to be too good to be true sometimes.

---

### Post by ofnuts on 2011-10-23
> **DarkAmbient said:**
> Don't mind sharing what I've written so far. (But only as an example of what not to do. *harrharr*). Also, added a log-system to my project now if anyone is interested. :)

And alas, that was kinda the same deal. Except my class is quite simple. Well, thanks for enlighten me. Java seems to be too good to be true sometimes.In Java, the logging is usually done through the "log4j" framework (see [http://logging.apache.org/log4j/1.2/](http://logging.apache.org/log4j/1.2/)) :P

Java is  very much used in business projects, where reinventing the wheel costs money. Hence all kinds of frameworks that can have some use in business projects are likely to be already available (some, I admit, with "business project" mass...).

---

### Post by DarkAmbient on 2011-10-23
> **ofnuts said:**
> In Java, the logging is usually done through the "log4j" framework (see [http://logging.apache.org/log4j/1.2/](http://logging.apache.org/log4j/1.2/)) :P

Java is  very much used in business projects, where reinventing the wheel costs money. Hence all kinds of frameworks that can have some use in business projects are likely to be already available (some, I admit, with "business project" mass...).

Cool, yea I figured there were some libraries/frameworks for logging in Java. I'm gonna hold on to that link. Resource-cheap logging I could use later on. :p

---

### Post by DarkAmbient on 2011-10-24
Thanks again for the help on read/write, properties and logging. I'm now using log4j and java.util.Properties instead of my own stuff. Works like a charm! Setting thread to solved, but I'll probably be back with more (newbie) questions about Java. 

:guitar:

---

