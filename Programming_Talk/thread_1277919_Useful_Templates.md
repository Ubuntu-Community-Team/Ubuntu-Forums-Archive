---
title: "Useful Templates"
date: 2009-09-28
forum: Programming Talk
---

### Post by Can+~ on 2009-09-28
Have you ever seen that folder inside the home directory named "Templates"? I use them in a daily basis, to the point I created some snippets that are quite useful, but I would like to expand my library (and share the ones I made)

**C** with common headers (at least for me).
```
//Standard Headers
#include <stdio.h>
//#include <stdlib.h>
//#include <string.h>
//#include <errno.h>

//Posix
//#include <unistd.h>			// Unix standard
//#include <sys/dirent.h>		// Directory functions
//#include <sys/ipc.h>			// Interprocess communication
//#include <sys/pthread.h>		// Posix Threads
//#include <sys/sem.h>			// Semaphores
//#include <sys/shm.h>			// Shared Memory
//#include <sys/signal.h>		// Signal handling
//#include <sys/socket.h>		// Socket bindings
//#include <sys/types.h>		// Unix types
//#include <sys/wait.h>			// Child process Wait


int main(int argc, char **argv)
{
	
	
	
	
	
	return 0;
}

```

**Python**: simple snippet.

```
#!/usr/bin/env python




if __name__ == "__main__":
	pass
```

**HTML:** w3 standard HTML 4.01 transitional utf-8 with optional CSS link.
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
	<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
	<meta name="keywords" content="HTML, tags, commands">
	<title>Index</title>
	
	<!--<link href="css/style.css" rel="stylesheet" type="text/css">-->
</head>
<body>

</body>
</html>
```

**LaTeX**: LaTeX empty document with cover, a table of contents, utf-8 spanish, and 3cm margin with geometry package.
```
\documentclass[letterpaper, 10pt]{article}
\usepackage[spanish]{babel}
\usepackage[utf8]{inputenc}
\usepackage[margin=3cm]{geometry}

\title{\textbf{Title} \\ Subtitle}
\author{Name}
\date{\today}

\begin{document}
\maketitle

\tableofcontents
\pagebreak

\section{Section 1}

\end{document}
```

---

