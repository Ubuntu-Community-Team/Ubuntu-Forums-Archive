---
title: "ruby, wrong number of arguments for initilize"
date: 2009-09-12
forum: Programming Talk
---

### Post by cybo on 2009-09-12
i have a peace of code in ruby and when i run i get the error below. the funny thing is that i took this code straight out of the textbook. can any one help me out

[I]song_test.rb:2:in `initialize': wrong number of arguments (3 for 0) (ArgumentError)
	from song_test.rb:2:in `new'
	from song_test.rb:2
[/I]
here is the code

song.rb
```

class Song
  def initilize(name, artist, duration)
    @name = name
    @artist = artist
    @duration = duration
  end

  attr_reader :name, :artist, :duration
end

```

song_test.rb
```

require 'song.rb'
my_song = Song.new("Worthy is the Lamb", "Hillsong", "300")
puts my_song.name
puts my_song.artist
puts my_song.duration

```

---

### Post by loell on 2009-09-12
def **[COLOR="Blue"]initi[COLOR="Red"]a[/COLOR]lize([/COLOR]**name, artist, duration) ;)

---

### Post by cybo on 2009-09-12
> **loell said:**
> def **[COLOR="Blue"]initi[COLOR="Red"]a[/COLOR]lize([/COLOR]**name, artist, duration) ;)

:D Thanks

---

