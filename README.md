# README

## Users table
| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| nickname           | string     | null: false |
| email              | string     | null: false, unique true, default: "" |
| encrypted_password | string     | null: false, default: "" |
| birth_date         | date       | null: false |
| first_name         | date       | null: false |
| first_name_kana    | string     | null: false |
| family_name        | string     | null: false |
| family_name_kana   | string     | null: false |

### Association
- has_many :items
- has_many :orders

## Items table
| Column       | Type       | Options                        |
| ------------ | ---------- | ------------------------------ |
| name         | string     | null: false                    |
| info         | text       | null: false                    |
| price        | integer    | null: false                    |
| category     | integer    | null: false                    |
| sales_status | integer    | null: false                    |
| shipping_fee | integer    | null: false                    |
| prefecture   | integer    | null: false                    |
| delivery     | integer    | null: false                    |
| user         | references | null: false, foreign_key: true |

###  Assosiation
- belongs_to :user
- has_one :order

##  orders table
| Column   | Type       | Options                        |
| -------- | ---------- | -------------------------------|
| user     | references | null: false, foreign_key: true |
| item     | references | null: false, foreign_key: true |

###  Assosiation
- belongs_to :user
- belongs_to :item
- has_one :address

## Addresses table
| Column | Type              | Options                        |
| ------ | ----------------- | ------------------------------ |
| postal_code   | string     | null: false                    |
| prefecture    | integer    | null: false                    |
| city          | string     | null: false                    |
| house_number  | string     | null: false                    |
| building      | string     |                                |
| phone_number  | string     | null: false                    |
| order         | references | null: false, foreign_key: true |

###  Assosiation
- belongs_to :order