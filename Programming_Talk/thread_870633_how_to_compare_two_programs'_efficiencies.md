---
title: "how to compare two programs' efficiencies ?"
date: 2008-07-26
forum: Programming Talk
---

### Post by dexter.deepak on 2008-07-26
i have always been wondering if i could compare two programs in statistical way,in terms of their (runtime) memory usage, speed,and other factors affecting efficiency. 
when i was learning C , i wanted to actually analyse two of my programs for the same objective, but using different algorithms; or even to compare speeds of simpler stuff like a call by value and call by reference...these things (at a lower level like mine) are not apparently visible.

is there a tool available that uses some programming parameters to compare 2 programs in same (or even) different languages ?

---

### Post by Tony Flury on 2008-07-26
Effectively you are talking about benchmarking.

Ideally to succesfully benchmark and algorithm, you need to write a harness which calls the algorithm multiple times (maybe even 100s of times), and measure items like CPU, I/O, elapsed times etc. Also depending on what you are trying to measure, you could well need to call the actual functions/methods rather than call an application (since when you call an application you have to factor in things like that amount of time needed to load the application from disk into RM etc.

However benchmarking is a high specialized activity, and depends on a lot of factors, and the exact techniques you need to use depend a lot on what you are trying to measure.

---

### Post by dexter.deepak on 2008-07-26
is benchmarking a manual technique ? or an automated one ?

---

### Post by Lster on 2008-07-26
I'd also advise you to have a look at stuff like computational complexities. It is possible that the sample test you make will be faster despite having a worse computational complexity, and thus, scale worse.

[http://en.wikipedia.org/wiki/Computational_complexity_theory](http://en.wikipedia.org/wiki/Computational_complexity_theory)
[http://en.wikipedia.org/wiki/Big_O_notation](http://en.wikipedia.org/wiki/Big_O_notation)

---

### Post by geirha on 2008-07-26
The time command is useful to compare runtime.
```

time ./prog1
time ./prog2

```

---

### Post by dexter.deepak on 2008-07-26
thanks a lot geirha..
i hope there is similar tool for estimating runtime memory too..

---

### Post by Wybiral on 2008-07-26
You're never going to get any useful data from this kind of low-level benchmarking. There is too much stuff going on from the operating system, other processes running, etc. If you want to know how efficient your algorithm is, listen to Lster and learn about algorithmic analysis.

If you want to know how your code does coefficiently, look at the assembly dump, learn which assembly operations are efficient for your target machine (the processor manual will tell you everything you need to know). But remember that this only applies to those operations on that architecture (which varies from machine to machine and will become unimportant as technology goes by), it's not going to tell you anything about your algorithm or how well it scales.

---

### Post by NathanB on 2008-07-26
We often perceive library functions as "black box" entities whose purpose is to "automagically" do a specific task for us.  This is often accompanied by a trust or assumption that the "black box" was designed with efficiency in mind.  Sometimes (when coding something non-trivial... a parser, a multimedia converter, etc.), we would definitely be better served by solving the issue by another means rather than calling a lib function a billion times.

Therefore, if *you* are coding a library, the efficiency of your functions **should** be a primary concern.  With this in mind, here is an example (in Ruby) of a benchmarking method.

**conv.rb**
[php]module Conv

    $lookup = %w{
 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
 10 11 12 13 14 15 16 17 18 19 1A 1B 1C 1D 1E 1F
 20 21 22 23 24 25 26 27 28 29 2A 2B 2C 2D 2E 2F
 30 31 32 33 34 35 36 37 38 39 3A 3B 3C 3D 3E 3F
 40 41 42 43 44 45 46 47 48 49 4A 4B 4C 4D 4E 4F
 50 51 52 53 54 55 56 57 58 59 5A 5B 5C 5D 5E 5F
 60 61 62 63 64 65 66 67 68 69 6A 6B 6C 6D 6E 6F
 70 71 72 73 74 75 76 77 78 79 7A 7B 7C 7D 7E 7F
 80 81 82 83 84 85 86 87 88 89 8A 8B 8C 8D 8E 8F
 90 91 92 93 94 95 96 97 98 99 9A 9B 9C 9D 9E 9F
 A0 A1 A2 A3 A4 A5 A6 A7 A8 A9 AA AB AC AD AE AF
 B0 B1 B2 B3 B4 B5 B6 B7 B8 B9 BA BB BC BD BE BF
 C0 C1 C2 C3 C4 C5 C6 C7 C8 C9 CA CB CC CD CE CF
 D0 D1 D2 D3 D4 D5 D6 D7 D8 D9 DA DB DC DD DE DF
 E0 E1 E2 E3 E4 E5 E6 E7 E8 E9 EA EB EC ED EE EF
 F0 F1 F2 F3 F4 F5 F6 F7 F8 F9 FA FB FC FD FE FF
    }

    ###  Converts a number to a hex-string
    ###  via the calculation method.
    ###
    def Conv.n2h_calc( number )
        if number > 255
            result = nil
        else
            result = "  "
            digit = 0
            while number != 0
                q, r = number.divmod( 16 )
                if r > 9
                    r += 55
                else
                    r += 48
                end
                result[ 1 - digit ] = r
                number = q
                digit += 1
            end
        end
        return result
    end

    ###  Converts a number to a hex-string
    ###  via a look-up table method.
    ###
    def Conv.n2h_table( number )
        if number > 255
            result = nil
        else
            result = $lookup[ number ]
        end
        return result
    end

end
[/php]

**compare.rb**
[php]require "conv.rb"

item = Array.new
8.times { |x| item[x] = rand( 256 ) }

start = Process.times
50000.times do
    8.times { |i| Conv.n2h_calc( item[i] ) }
end
stop = Process.times
duration = stop.utime - start.utime

print "Seconds for n2h_calc() to run: "
puts duration

start = Process.times
50000.times do
    8.times { |i| Conv.n2h_table( item[i] ) }
end
stop = Process.times
duration = stop.utime - start.utime

print "Seconds for n2h_table() to run: "
puts duration
[/php]

Nathan.

---

