# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| email              | string | null: false |
| encrypted_password | string | null: false |
| name               | string | null: false |
| profile            | text   | null: false |
| occupation         | text   | null: false |
| position           | text   | null: false |

- has_many :prototypes_users
- has_many :prototypes, through: :prototypes_users
- has_many :comments

## prototypes テーブル

| Column     | Type       | Options                         |
| ---------- | ---------- | ------------------------------- |
| title      | string     | null: false                     |
| catch_copy | text       | null: false                     |
| concept    | text       | null: false                     |
| user       | references | null: false, foreign_key: true  |

### Association

- has_many :prototypes_users
- has_many :users, through: :prototypes_users
- has_many :comments

## prototypes_users テーブル

| Column     | Type       | Options                        |
| ---------- | ---------- | ------------------------------ |
| user       | references | null: false, foreign_key: true |
| prototypes | references | null: false, foreign_key: true |

### Association

- belongs_to :prototypes
- belongs_to :user

## comments テーブル

| Column    | Type       | Options                        |
| --------- | ---------- | ------------------------------ |
| content   | string     |                                |
| user      | references | null: false, foreign_key: true |
| prototype | references | null: false, foreign_key: true |

### Association

- belongs_to :prototypes
- belongs_to :user