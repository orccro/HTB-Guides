# A guide for the HTB CTF challenge "Sightless"

### My target IP: 10.10.11.32  (your target IP might vary), using Kali Linux

#### Hunt for the user flag.txt

First we being with a typical nmap scan to see what is going on.  I will use rustscan for the initial scan.  If you do not have rustscan the follow command will install it:
```
wget https://github.com/RustScan/RustScan/releases/download/2.0.1/rustscan_2.0.1_amd64.deb
sudo dpkg -i rustscan_2.0.1_amd64.deb
```
You can then verify the installation by using:
```rustscan --version``` to confirm installation.

Once rustscan is ready to go we being with command ```rustscan -a 10.10.11.32 -- -sC -sV```

The result of the scan can be seen below:

![Initial Scan](./images/Sightless%20-%20initial%20scan.png)

The take away from the scan is that ports 21, 22, and 80 are open.  It is unlikely we will have any luck directly attacking ports 21 and 22, so lets being our exploration at port 80.  Within the port 80 result we can see that the scan has recorded a redirect from our target, ```http-title: Did not follow redirect to http://sightless.htb/``` we will need to accomidate this within our host file.  If we go directly to the target ip via a web browser we hit a dead end.  So lets fix this by using the following:
```nano /etc/hosts```
within the file end the target ip & name of site (sightless.htb) ```10.10.11.32  sightless.htb```  save file and we're ready




