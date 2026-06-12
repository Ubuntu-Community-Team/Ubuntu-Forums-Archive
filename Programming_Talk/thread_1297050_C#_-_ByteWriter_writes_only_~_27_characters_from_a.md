---
title: "C# - ByteWriter writes only ~ 27 characters from a 30 char string."
date: 2009-10-21
forum: Programming Talk
---

### Post by OpenGuard on 2009-10-21
[COLOR=Black]Slot = 30 bytes ..[/COLOR]
If a string is 10 char long, I need to fill the rest 20 bytes with something else ( to keep the structure untouched ). I'm currently using ByteWriter, but instead of 10 chars + 20 whitespaces, I get 10 chars + ~ 15 whitespaces.

As an example, this screenshot - if I'll remove " ( Single Edit ) " and save it, I'll get " Sadness _________           it ) " ( _ = whitespace ).

Any ideas ?

```
        public void saveTitle(string title)
        {
            BinaryWriter oStream = new BinaryWriter(File.Open(file, FileMode.Open));

            if (title.Length < 30)
            {
                for (int i = 0; i < 30 - title.Length; i++)
                {
                    title += "\0";
                }
            }

            byte[] byteTitle = new byte[title.Length];
            int id3_start = getFileLength() - 125;

            for (int i = 0; i < title.Length; i++)
            {
                byteTitle[i] = Convert.ToByte(title[i]);
            }

            oStream.BaseStream.Seek(id3_start, SeekOrigin.Begin);
            oStream.Write(byteTitle, 0, byteTitle.Length);

            oStream.Close();
        }
```[IMG]http://i38.tinypic.com/11ttrwk.png[/IMG]


Update :: Replaced whitespace with \0 and Title slot now seems to work as expected, tough, it raised another problem .. Now I can't shorten the artist slot - if I save it with a longer string than the current one, everything is ok, but I can't delete it ( I mean, if I remove 5 chars and save it, they will still be there ) .. Any ideas ? Functions are 100% identical ( except variable names ).

---

