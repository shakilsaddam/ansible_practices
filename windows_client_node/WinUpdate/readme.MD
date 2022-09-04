Step-by-step Instructions: Ansible - how to connect to windows ansible host?
============================================================================

Client Node (Windows Part)
-------------------------
1. Download the script from here: https://github.com/ansible/ansible/blob/devel/examples/scripts/ConfigureRemotingForAnsible.ps1
2. Once you donwload the ConfigureRemotingForAnsible.ps1 file the following command from command line should do the job:
/t
```
powershell.exe -File ConfigureRemotingForAnsible.ps1
```
Link: https://stackoverflow.com/questions/38259422/in-ansible-how-to-connect-to-windows-host

3. The above script may not be run due to permission issue. To permit executing script on Windows Powershell, execute the below command on PowerShell first.
```
set-ExecutionPolicy RemoteSigned -Scope CurrentUser 
```
Link: https://www.c-sharpcorner.com/article/how-to-fix-ps1-can-not-be-loaded-because-running-scripts-is-disabled-on-this-sys/


Control Node (Ubuntu Server Part):
----------------------------------
Ansible is already installed in our ubuntu server and client nodes are reachable from the ubuntu server.

1. ansible.windows.win_updates module – Download and install Windows updates
```
ansible-galaxy collection install ansible.windows
```
2. Ansible Inventory(`/etc/ansible/hosts`) needs to updated accordingly. An example inventory file is available here.
3. You can find all the required information about ansible `win_update` module from here: https://docs.ansible.com/ansible/latest/collections/ansible/windows/win_updates_module.html

4. How to execute the ansible playbook? Just execute the following command
```
ansible-playbook win-updt-check-playbook.yaml
```