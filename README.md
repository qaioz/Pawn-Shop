# Pawn-Shop


Api for the pawn shop owner

branches:
    adress and name
customers:
    name, personl number

Items:
    Each item is meant to be unique and different from each other.
    THere are 3 types of items:
        1. Jewelry
        2. Cars
        3. Tech

    Jewelry:
        precious metal1, precious metal2, precious stone1, precious stone2
    Cars:
        model, brand, year, odometer reading, odometer unit
    Tech:
        type, brand, damage description

    Each item must be saved in database alongside with the following information:
        1. Money that has to be returned in total (Here we mean price after interest was added after all months)
        2. Customer who pawned the item
        3. Branch where the item was pawned
        4. Date when the item was pawned
        5. Duration in months
        6. Amount of money for each month
        7. day of the month when the payment has to be made
        8. Every associated payment
        9. Item status: pawned, returned, sold

Payment rules:
    0. Total money that has to be returned including interest is calculated by the employee. Details are not relevant.
        T = total money that has to be returned

    1.Customer can choose how many months he wants to pawn the item for.
        i is in rande [1, M]
        M = amount of months
        Pay attention that i does not mean january, february, march, etc, it means wich month of the loan it is.

    2.Amount of money for each month is calculated by the following formula:
        F2 = T/M

    3. Day of the month when the payment has to be made in each month is calculated by the following formula:
        D = max(pawned day, 28)
        meaning that if the pawned day is 31, then the payment day will be 28th of each month.
        I think every real world loan is like this.

    4. Person can make several payments in a month, each payment can be 1 dollar and more.

    5. Total amount that was paid in a month i is calculated by the following formula:
        F5(i) = sum of all payments in a month i

    6. Total money that was paid for so far is calculated by the following formula:
        F6 = sum of all payments

    7. Total amount that has to be paid by end of current month i, is calculated by the formula
        F7(i) = F2 * i

    8. To check if the enough money was paid by the end of current month i, we use the following formula:
        F8 = F6 >= F7(i)


