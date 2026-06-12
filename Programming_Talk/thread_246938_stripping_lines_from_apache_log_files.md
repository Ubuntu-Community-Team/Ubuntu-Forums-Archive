---
title: "stripping lines from apache log files"
date: 2006-08-30
forum: Programming Talk
---

### Post by takayuki on 2006-08-30
Hi,

i've got a logfile about 50k lines long.

i'd like to use sed to strip lines containing .jpeg, .gif, .css, images, jpegs, .ico

so far, i've been entering each command one by one, but i'd like to have a small bash script that'd do it all.

this is what i've got so far.

[PHP]sed -e '/\.jpg/d' | 

sed -e '/\.JPG/d' | 

sed -e '/images/d' |

sed -e '/\.css/d' |

sed -e '/\.gif/d' |

sed -e '/\.jpegs/d' |

sed -e '/\.ico/d' |

sed -e '/\.png/d' < input.txt > output.txt[/PHP]

which doesn't work!

how can i string each of the sed commands together?

how can i use a variable for input text so i could do something like this?

[PHP]./logstripper input.txt[/PHP]

thanks for any help!

takayuki

---

### Post by Woei on 2006-08-30
> **takayuki said:**
> Hi,

i've got a logfile about 50k lines long.

i'd like to use sed to strip lines containing .jpeg, .gif, .css, images, jpegs, .ico

so far, i've been entering each command one by one, but i'd like to have a small bash script that'd do it all.

this is what i've got so far.

[PHP]sed -e '/\.jpg/d' | 

sed -e '/\.JPG/d' | 

sed -e '/images/d' |

sed -e '/\.css/d' |

sed -e '/\.gif/d' |

sed -e '/\.jpegs/d' |

sed -e '/\.ico/d' |

sed -e '/\.png/d' < input.txt > output.txt[/PHP]

which doesn't work!

how can i string each of the sed commands together?

how can i use a variable for input text so i could do something like this?

[PHP]./logstripper input.txt[/PHP]

thanks for any help!

takayuki

You can either add multiple '-e' command line options to a single sed command, or separate operations inside a single '-e' command with ;
```

sed -e '/\.gif/d ; /\.css/d ; /\.ico/d'

```
```

sed -e '/\.gif/d' -e '/\.css/d' -e '/\.ico/d'

```

You can put that sed command in a file, put #!/bin/sh at the top, and add "$@" at the end of your sed script.
```

#/bin/sh
sed -e '/\.gif/d ; /\.css/d ; /\.ico/d' "$@"

```

But input redirection like you're doing now works just as well.

---

### Post by takayuki on 2006-08-30
thanks Woei!

sed -e '/\.gif/d ; /\.css/d ; /\.ico/d ; /\.JPG/d ; /\.jpg/d ; /.png/d ; /images/d ; /jpegs/d' < "$@" > stripped.txt

worked great.

in my previous attempts my syntax was off.  i knew i could separate with semicolons, but just didn't have a good example.  thanks for the help.

regards,

takayuki

---

