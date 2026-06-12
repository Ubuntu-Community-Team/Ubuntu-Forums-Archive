---
title: "Java Program: organize music folders"
date: 2009-12-23
forum: Programming Talk
---

### Post by prem1er on 2009-12-23
I am working on creating my first 'useful' piece of software for my own personal use. I am not completely new to Java, but I am definitely still learning. I am writing a small program to help keep my music organized on my file system and since I have most of the functionality working I figured I would share it here for you to take a look at and let me know what you think, or if anyone needs it for their own use.

My program is set to watch a specific directory for new folders being added. In my case, it watches my music directory for newly ripped or downloaded albums. It copies the files to a new location and renames them based on artist, album, and release year. This way I don't have to manually move/rename all the files and I can remove them from my download directory once I am finished seeding. 

I'm using a java package called Jaudiotagger to read ID3 tags.

I haven't set up a logger yet, so excuse all the sys-outs.

```
package com.organize.music;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Iterator;
import java.util.List;

import org.jaudiotagger.audio.AudioFileIO;
import org.jaudiotagger.audio.mp3.MP3File;
import org.jaudiotagger.tag.id3.ID3v24Frames;
import org.jaudiotagger.tag.id3.ID3v24Tag;

public class OrganizeMusic {

    private static final String WATCH_DIR = "/home/user/download";

    private static final String OUTPUT_DIR = "/home/user/music";
    
    private File albumInputFile;

    public OrganizeMusic() {}

    /**
     * @param args
     */
    public static void main(String[] args) {
        try {
            OrganizeMusic app = new OrganizeMusic();
            System.out.println("Process running ..");
            System.out.println("Directory to watch: " + WATCH_DIR + " ..");
            app.watchDirectory();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    //Method to watch a specific directory for changes in the timestamp.
    public void watchDirectory() throws InterruptedException {
        File newFolder = new File(WATCH_DIR);
        List<String> fileList = new ArrayList<String>(Arrays.asList(newFolder.list()));
        List<String> tempFileList = null;
        long lastModified = newFolder.lastModified();
        System.out.println("Directory last modified: " + lastModified + " ..");
        String newAlbum = null;
        while (true) {
            if (newFolder.lastModified() > lastModified) {
                System.out.println("New folder added ..");
                tempFileList = new ArrayList<String>(Arrays.asList(newFolder.list()));
                tempFileList.removeAll(fileList);
                newAlbum = tempFileList.get(0);
                System.out.println("Folder name: " + newAlbum + " ..");
                findMP3File(newAlbum);
                fileList = Arrays.asList(newFolder.list());
                tempFileList.clear();
                lastModified = newFolder.lastModified();
            }
            Thread.sleep(2000);
        }
    }

    //Inspects the new folder for any .mp3 files that it may contain.
    public void findMP3File(String albumName) {
        String pathToAlbum = WATCH_DIR + "/" + albumName;
        this.albumInputFile = new File(pathToAlbum);
        List<String> fileList = new ArrayList<String>(Arrays.asList(albumInputFile.list()));
        String mp3String = null;
        Iterator<String> it = fileList.iterator();
        System.out.println("Locating an input .mp3 file ..");
        while ( it.hasNext() && mp3String == null ) {
            mp3String = it.next();
            int subStringStart = mp3String.length() - 4;
            if ( mp3String.substring(subStringStart, mp3String.length()).equals(".mp3") ) {
                try {
                    System.out.println("Using: " + mp3String + " as input ..");
                    File mp3File = new File(pathToAlbum + "/" + mp3String);
                    System.out.println("Reading id3 tag ..");
                    readIDTag(mp3File);
                } catch (Exception e) {
                    e.printStackTrace();
                }

            } else {
                System.out.println("No .mp3 files found, new folder is being ignored ..");
                mp3String = null;
            }
        }
    }
    
    //Reads the tag for any information I may need and stores in in an Mp3Data object.
    public void readIDTag(File mp3) throws Exception {
        MP3File mp3File = (MP3File) AudioFileIO.read(mp3);
        Mp3Data audioData = new Mp3Data();

        if ( mp3File.hasID3v2Tag() ) {
            System.out.println("ID3v2 tag found ..");
            ID3v24Tag v24Tag = mp3File.getID3v2TagAsv24();
            audioData.setArtist(v24Tag.getFirst(ID3v24Frames.FRAME_ID_ARTIST));
            audioData.setAlbum(v24Tag.getFirst(ID3v24Frames.FRAME_ID_ALBUM));
            audioData.setYear(v24Tag.getFirst(ID3v24Frames.FRAME_ID_YEAR));

            System.out.println("Artist: " + audioData.getArtist() + " ..");
            System.out.println("Album: " + audioData.getAlbum() + " ..");
            System.out.println("Release year: " + audioData.getYear() + " ..");
        } else {
            System.out.println("No ID3 tag ..");
        }
        createNewDirectories(audioData);
    }

    //Creates the new directory on the file system where the file will be moved. 
    //Structure example. ../music/Artist/Year - Album Name
    public void createNewDirectories(Mp3Data audioData) throws IOException {
        String artist = audioData.getArtist();
        String album = audioData.getAlbum();
        String year = audioData.getYear();
        
        StringBuffer tempArtist = null;
        if ( artist.startsWith("The") ) {
            String[] artistArray = artist.split(" ");

            for (int i = 1; i >= artistArray.length; ++i) {
                tempArtist = tempArtist.append(artistArray[i]);
            }
            tempArtist.append(", The");
            artist = tempArtist.toString();
        }

        File artistDirectory = new File(OUTPUT_DIR + "/" + artist);
        File albumDirectory = new File(OUTPUT_DIR + "/" + artist + "/" + year + " - " + album);
        
        if ( !artistDirectory.exists() ) {
            System.out.println("Creating artist directory: " + OUTPUT_DIR + "/" + artist + " ..");
            artistDirectory.mkdir();
        } else {
            System.out.println("Artist already exists: " + OUTPUT_DIR + "/" + artist + " ..");
        }
        
        if ( albumDirectory.exists() ) {
            System.out.println("Artist and album already exist on system ..");
            System.out.println(OUTPUT_DIR + "/" + artist + "/" + year + " - " + album);

        } 
        System.out.println("Creating album directory: " + OUTPUT_DIR + "/" + artist + "/" + year + " - " + album);
        System.out.println("Copying files to new album directory ..");
        copyAlbumFiles(this.albumInputFile, albumDirectory);
    }
    
    //Copies all of the files within the album to its new location.
    public void copyAlbumFiles(File sourceLocation , File targetLocation)
    throws IOException {
        
        if ( sourceLocation.isDirectory() ) {
            if ( !targetLocation.exists() ) {
                targetLocation.mkdir();
            }
            
            String[] children = sourceLocation.list();
            for (int i=0; i<children.length; i++) {
                copyAlbumFiles(new File(sourceLocation, children[i]),
                        new File(targetLocation, children[i]));
            }
        } else {
            
            InputStream in = new FileInputStream(sourceLocation);
            OutputStream out = new FileOutputStream(targetLocation);

            byte[] buf = new byte[1024];
            int len;
            while ((len = in.read(buf)) > 0) {
                out.write(buf, 0, len);
            }
            in.close();
            out.close();
        }
    }
}
```

---

### Post by Queue29 on 2009-12-23
Haven't actually run it yet, but it does look like a solid solution. To go further you could turn it into a daemon or cron job, or even extend your favorite cd ripper to run immediately after ripping a cd, and then send those modifications up stream. :cool:

---

### Post by prem1er on 2009-12-23
Thanks. I plan on packaging it with a simple bash script that allows someone to run it from anywhere. I probably will ask for an input and output directory as parameters.

---

### Post by romihim on 2011-11-09
> **prem1er said:**
> Thanks. I plan on packaging it with a simple bash script that allows someone to run it from anywhere. I probably will ask for an input and output directory as parameters.

Hi,

I am also developing a program to manage my music , esp. wrt to  bulk editing of tags, among other tasks. I really like the concept of automatically taking the mp3s from downloads and copying them to correct place. If you have made the program final, can you give me its link. 
It would be of great help .

Thanks

---

### Post by ofnuts on 2011-11-09
> **prem1er said:**
> I am working on creating my first 'useful' piece of software for my own personal use. I am not completely new to Java, but I am definitely still learning. I am writing a small program to help keep my music organized on my file system and since I have most of the functionality working I figured I would share it here for you to take a look at and let me know what you think, or if anyone needs it for their own use.

My program is set to watch a specific directory for new folders being added. In my case, it watches my music directory for newly ripped or downloaded albums. It copies the files to a new location and renames them based on artist, album, and release year. This way I don't have to manually move/rename all the files and I can remove them from my download directory once I am finished seeding. 

I'm using a java package called Jaudiotagger to read ID3 tags.

I haven't set up a logger yet, so excuse all the sys-outs.


Some random comments:


[LIST]
[*] Most of your print statements are pointless. There is nothing that enforces that what your print is really what you use. For instance:
[/LIST]
 ```

File albumDirectory = new File(OUTPUT_DIR + "/" + artist + "/" + year + " - " + album);
....        
 System.out.println("Creating album directory: " + OUTPUT_DIR + "/" + artist + "/" + year + " - " + album);

```should better be:
```

File albumDirectory = new File(OUTPUT_DIR + "/" + artist + "/" + year + " - " + album);
 ....        
 System.out.println("Creating album directory: " + albumDirectory.getCanonicalPath());

```
[LIST]
[*]Replace the hardcoded file/directory by MessageFormat string, and be ready to get these MessageFormat strings from a properties file (this wil likely be the first request by users if you make the code public):
[/LIST]
 ```

static String albumFormat="{0}/{1}/{4}-{2}";
albumDirName=MessageFormat.format(albumFormat,[OUTPUT_DIR,artist,album,cdpart,year);

```

[LIST]
[*]Your file copy performance can be improved: you can use significantly larger buffers, and maybe have  a look at  the java.nio package which AFAIK is meant for high performance I/O.
[*]To test for a file extension use String.endsWith(). You may also want to use another "properties" item for the supported file extensions (to handle .ogg, .flac)...
[*]WATCH_DIR & OUTPUT_DIR should be a mix of properties and user home directory (maybe recognize "~" and replace by System.getProperty("user.home")
[*]Your test for "newFolder.lastModified()" won't work if an old directory is moved in WATCH_DIR. What really counts is the inode modification date (the thing you get with "ls -c").
[*]IRL your program is is going to cause you a lot of grief as a "watcher" because it will try to copy/move things that are not complete (it takes more than 2 seconds to rip/download a MP3).
[*]I'm not convinced your program will do the right thing when it starts if your forgot to empty WATCH_DIR (It think it will copy everything again). IMHO it should copy/move the files to their target directory and keep WATCH_DIR empty. If you keep the source files on the side it means you don't trust your own code :) (and if you don't, don't expect others to do so). Of course during development and testing you may lose a couple of files but once this is done you should display some self-confidence.
[/LIST]
I know these comments may hurt a bit but "c'est le métier qui rentre" (*) as we say in my country. Not that bad for a first shot actually.

(*) it's the job experience that settles in

---

