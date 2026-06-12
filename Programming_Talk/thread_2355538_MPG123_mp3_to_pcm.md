---
title: "MPG123 mp3 to pcm"
date: 2017-03-13
forum: Programming Talk
---

### Post by atton on 2017-03-13
I think the title says it all, but I will briefly explain what I am trying to do. I am trying to use mpg123 to produce raw pcm data from an mp3 file. I've come quite close to actually making this work but I have run into the issue of distortion. Anything produced by the code below is distorted to hell when played in audacity, as to why I am unsure nor do I know how to fix it. Any advice would be much appreciated. 


```
int decodeMp3(string filename, string outString)
{
    mpg123_handle *mh;
    //unsigned char *buffer;
    unsigned char *buffer;
    size_t buffer_size;
    size_t done;
    int err;

    int channels, encoding;
    long rate;

    mpg123_init();
    mh = mpg123_new(NULL, &err);
    buffer_size = mpg123_outblock(mh);
    buffer = (unsigned char*)malloc(buffer_size * sizeof(unsigned char));

    /* open the file and get the decoding format */
    mpg123_open(mh, filename.c_str());
    mpg123_getformat(mh, &rate, &channels, &encoding);

    /* set the output format and open the output device */
    int m_bits = mpg123_encsize(encoding);
    int m_rate = rate;
    int m_channels = channels;
    std::ofstream out(outString.c_str());
    /* decode and play */
    for (int totalBtyes = 0; mpg123_read(mh, buffer, buffer_size, &done) == MPG123_OK; ) 
    {
        char *data = new char[done + 1];
        for (int i = 0; i != done; i++)
        {
            char tst = static_cast<char>(buffer[i]);
            //cout << done << " " << sizeof(data) << endl;
            out << tst;
        }

        totalBtyes += done;
    }
    //out << buffer[i];
    
    cout << "Buffer size " << buffer_size << endl;
    cout << "Done " << done << endl;
    cout << "err " << err << endl;
    cout << "channels " << channels << endl;
    cout << "encoding " << encoding << endl;
    cout << "Rate " << rate << endl;
    cout << "m_bits " << m_bits << endl;
    cout << "m_rate " << m_rate << endl;
    cout << "m_channels " << m_channels << endl;
    cout << "The size of buffer " << sizeof(buffer) << endl;
    /* clean up */
    free(buffer);
    out.close();
    mpg123_close(mh);
    mpg123_delete(mh);
    mpg123_exit();
    return 0;
}
```

---

### Post by norobro on 2017-03-14
I don't have audacity installed to try but two .mp3 files I converted with your code sounded fine with "play" and "vlc".```
[FONT=monospace][COLOR=#000000]vlc --demux=rawaud --rawaud-channels 2  filename.pcm[/COLOR][/FONT]
``````
[FONT=monospace][COLOR=#000000]play -t raw -r "bitrate" -e signed -b 16 -c 1 filename.pcm[/COLOR][/FONT]
```

---

