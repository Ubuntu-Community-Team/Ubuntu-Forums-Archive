---
title: "How to retrieve URL input from rich texbox in C#"
date: 2012-05-12
forum: Programming Talk
---

### Post by Tarast on 2012-05-12
I am writing a security tool as a part of my project for the university, I wan to allow a user to enter any url address. The problem is i cant figure out how to do that.

 // Verify URL is vaild
            try
            {
                // Prepare request
                HttpWebRequest request = (HttpWebRequest)
                WebRequest.Create("http://www.kolobok.ru/");

                // Execute request
                using (HttpWebResponse responce = (HttpWebResponse)request.GetResponse())
                {
                    // Check if URL accepting requests
                    if (responce.StatusCode == HttpStatusCode.OK)
                    {
                        MessageBox.Show("URL Has Been Verified, Commencing Attack!");
                    }
                }
            }
            // Catch Errors
            catch (Exception loi)
            {
                MessageBox.Show(loi.Message);
            }

Any ideas or suggestions would really help

---

