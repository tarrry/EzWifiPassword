import subprocess

def close_terminal():
    close = False
    while not close:
        print("""""")
        user_input = input("Press enter to exit the terminal: ")
        if user_input.lower() == '':
            close = True

data = subprocess.check_output(['netsh', 'wlan', 'show', 'profiles']).decode('utf-8').split('\n')
allProfiles = [i.split(":")[1][1:-1] for i in data if "All User Profile" in i]

for i in allProfiles:
    results = subprocess.check_output(['netsh', 'wlan', 'show', 'profile', i, 'key=clear']).decode('utf-8').split('\n')
    results = [b.split(":")[1][1:-1] for b in results if "Key Content" in b]
    try:
        print("{:<30}|  {:<}".format(i, results[0]))
    except IndexError:
        print("{:<30}|  {:<}".format(i, ""))

close_terminal()
