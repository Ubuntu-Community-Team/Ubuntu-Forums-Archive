---
title: "I need help with a simple HTTP server in bash."
date: 2009-07-01
forum: Programming Talk
---

### Post by Yuzem on 2009-07-01
I have a simple http server in bash and it works great for html content but when trying to send some images only the first one get displayed on the browser.
Any idea what the problem could be?
Here is the code:
```

# web.sh -- http://localhost:9009/
#folder=folder_with_imges
cd $folder

RESP=/tmp/webresp
[ -p $RESP ] || mkfifo $RESP

while true ; do
	( cat $RESP ) | nc -l -p 9009 | (
		REQ=$(while read L && [ " " "<" "$L" ] ; do echo "$L" ; done)
		echo "$REQ"
		echo "[`date '+%Y-%m-%d %H:%M:%S'`] ${REQ%%$'\n'*}"

		REQ=${REQ#* } REQ=${REQ% HTTP*}

		if [[ $REQ = *png ]]; then
			file=.$REQ
			size=$(find $file -printf '%s')

			{
				echo HTTP/1.0 200 OK
				echo Cache-Control: private
				echo Content-Type: image/jpeg
				echo Connection: Close
				echo Content-Length: $size
				echo
				cat $file
				echo
			} > $RESP
		else
			page=$(
				for i in movies books music pictures; do
					echo "<img src='$i.png'></div>"
				done
			)

			{
				echo HTTP/1.0 200 OK
				echo Cache-Control: private
				echo Content-Type: html
				echo Server: bash/2.0
				echo Connection: Close
				echo Content-Length: ${#page}
				echo

				echo "$page"
			} > $RESP
		fi
	)
done

```

---

