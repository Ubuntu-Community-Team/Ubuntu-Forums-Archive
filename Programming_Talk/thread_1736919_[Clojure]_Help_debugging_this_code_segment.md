---
title: "[Clojure] Help debugging this code segment?"
date: 2011-04-22
forum: Programming Talk
---

### Post by josephellengar on 2011-04-22
Hi. I'm just learning Clojure and have a strange error that I have been unable to debug. Any help would be appreciated.

This code segment:

```

(defn getClosest 
  "gets the closest 50 locations in the file fName and writes them out by sending a function to the agent"
  [fName]
  (let [sorted (sort-by sortFn (makeStructs fName))
        ]
        (def topFifty (take 50 sorted))
     ;send an async message to the agent
     (send-off mAgent 
        (fn [mState] ;makes a new function to send to the agent, write out sorted to the file
          (dorun 
             (map #(. mState write %1) topFifty)
          mState) ;returns the agent's state
        )
        )
     )
)

```

Is throwing this error message (At or around the line above with the map):

```

Caused by: java.lang.IllegalArgumentException: Don't know how to create ISeq from: java.io.BufferedWriter

```

---

### Post by josephellengar on 2011-04-23
bump

---

### Post by crush304 on 2011-04-23
guessing the error is from the mState inside the dorun

(dorun 
    (map #(. mState write %1) topFifty)
mState)

->

(dorun 
    (map #(. mState write %1) topFifty))
mState

---

### Post by josephellengar on 2011-04-23
> **crush304 said:**
> guessing the error is from the mState inside the dorun

(dorun 
    (map #(. mState write %1) topFifty)
mState)

->

(dorun 
    (map #(. mState write %1) topFifty))
mState

Thank you very much for your help. Now it gives a different message:

```

     (send-off mAgent 
        (fn [mState] ;makes a new function to send to the agent, write out sorted to the file
          (dorun 
             (map #(. mState write %1) topFifty))
          mState ;returns the agent's state
        )
        )

```

yields:

```

Caused by: java.lang.RuntimeException: java.lang.IllegalArgumentException: No matching method found: write for class java.io.BufferedWriter

```

I am 100% certain that java.io.BufferedWriter does have a write method, based on the [documentation]("http://download.oracle.com/javase/1.5.0/docs/api/java/io/BufferedWriter.html").

---

