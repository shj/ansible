# ansible

## build.sh
- ディレクトリを作成するためのシェル

## パスワードの暗号化
- パスワードは以下のフォーマットで記述する
  ```
  ansible_ssh_user: root
  ansible_ssh_pass: xxxxxxxx
  ```
- 以下のコマンドでパスワードファイルを暗号化する
  ```
  ansible-vault encrypt <ファイル名>
  ```
- 複合化する場合は以下のコマンドを使う
  ```
  ansible-vault decrypt <ファイル名>
  ```
- ansible.cfgに以下の項目を追加している
  ```
  ask_vault_pass = True
  ```
- パスワードファイルは基本的にgroup_varsで設定しておき、個別に変更が必要な場合はhost_varsで上書きする

## ディレクトリ構成
```
ansible
├── ansible.cfg
├── build.sh
├── inventories
│   └── production
│       ├── group_vars
│       │   ├── all
│       │   └── group01
│       │       └── auth.yml
│       ├── host_vars
│       │   └── host01
│       └── hosts
└── playbooks
    ├── host01.yml
    └── roles
        └── group01
            └── test
                ├── defaults
                ├── files
                ├── handlers
                ├── meta
                ├── tasks
                │   └── main.yml
                ├── templates
                └── vars

```
