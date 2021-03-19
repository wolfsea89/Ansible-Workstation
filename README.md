Workstation-Ansible
=========
Przygotowanie stacji roboczej

Uwaga:
```
Testowane na Ubuntu 20.04
```

Playbook składa się z dwóch rul:
  - Przygotowanie stacji roboczej
  - Konfiguracja profilu użytkownika

Przygtowanie stacji roboczej
=========
1. Konfiguracja sudo (nie pytanie o hasło)
2. Konfiguracja usługi SSH
3. Kopiowane certyfikatu CA
4. Instalowanie narzędzi
5. Instalowanie Google Chrome
6. Instalowanie Visual Studio Code
7. Instalowanie Ansible
8. Instalowanie VirtualBox
9. Instalowanie Enpass
10. Instalowanie Docker
11. Instalowanie Helm
12. Aktualizacja systemu (Ubuntu)
13. Ustawienie Hostname

Konfiguracja profilu użytkownika
=========
1. Tworzenie użytkownika
2. Konfiguracja profilu użytkownika (.bashrc)
3. Konfiguracja Git
4. Kopiowanie kluczy SSH
5. Dodawanie Certyfikatu CA (Google Chrome)
6. Konfiguracja Visual Studio Code

Konfiguracja inventory
=========
Konfiguracja Visual Studio Code

```
inventory_group_workstastions_user_profile:
  vscode:
    extenssions:
      - alefragnani.project-manager
      - CoenraadS.bracket-pair-colorizer-2
      - donjayamanne.githistory
      - eamodio.gitlens
      - haaaad.ansible
      - janjoerke.jenkins-pipeline-linter-connector
      - marlon407.code-groovy
      - mhutchie.git-graph
      - redhat.vscode-yaml
      - secanis.jenkinsfile-support
      - wholroyd.jinja
```
Lista użytkowników
```
inventory_group_all_users:
  none: # musi być więcej niż 1 element
  mrachuna:
    gecos: "Maciej Rachuna"
    state: present
    git:
      name: "Maciej Rachuna"
      email: rachuna.maciej@gmail.com
    ssh:
      private_key: ""
      public_key: ""
```
Konfiguracja hosta
```
ansible_host: developerstation.rachuna.net

invnetory_host_users:
  - name: mrachuna
    groups:
      - adm
      - docker
      - sudo
  - name: usertest
    groups: []
```
Playbooki
=========
prepareOs.yml        - przygotowanie systemu oraz konfiguracja profilu użytkownika
configureProfile.yml - konfiguracja profilu uzytkowników
