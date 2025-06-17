# Systemy czasu rzeczywistego - projekt

1. **Tytuł modelu**:
    - System obsługi biblioteki

2. **Dane studenta**:
    - Piotr Zborowski
    - <zborowsk@student.agh.edu.pl>

3. **Opis modelowanego systemu**:
    - Opis ogólny

    ```txt
    System rezerwacji książek w bibliotece umożliwia użytkownikom przeglądanie dostępności książek oraz składanie żądań rezerwacji. Obsługuje również działania związane z zatwierdzaniem rezerwacji, aktualizacją statusu książek oraz logowaniem zdarzeń. Komponenty systemu współpracują w środowisku czasu rzeczywistego, komunikując się za pomocą urządzeń wejścia/wyjścia oraz magistrali danych.
    ```

    - Opis dla użytkowników

    ```txt
    Czytelnik może:

    - Sprawdzić dostępność książki,
    - Zarezerwować książkę,
    - Otrzymać informację o powodzeniu lub niepowodzeniu rezerwacji.
    
    System automatycznie:
    
    - Weryfikuje dostępność książki,
    - Odrzuca rezerwację, jeśli użytkownik przekroczył limit,
    - Wysyła odpowiedź w czasie rzeczywistym,
    - Rejestruje każde działanie w dzienniku zdarzeń.
    ```

   4. **Komponenty**:
    - **data**:
        - BookID, UserID – identyfikatory książek i użytkowników,
        - BookStatus – status książki (dostępna, wypożyczona, zarezerwowana, zagubiona),
        - ReservationRequest, ReservationResponse – żądania i odpowiedzi związane z rezerwacją książek,
        - EventLogEntry – wpisy logujące zdarzenia w systemie,
    - **system**:
        - system LibrarySystem – główny system biblioteczny odpowiedzialny za zarządzanie użytkownikiem, książkami i rezerwacjami,
    - **device**:
        - device user_terminal – terminal użytkownika służący do komunikacji z systemem,
        - device book_scanner – skaner książek wykrywający identyfikator książki,
        - device db_server – serwer bazy danych obsługujący zapytania i odpowiedzi,
    - **processor**:
        - processor CPU – procesor systemu bibliotecznego odpowiedzialny za przetwarzanie procesów,
    - **memory**:
        - memory RAM – pamięć operacyjna systemu, używana przez wszystkie procesy,
    - **bus**:
        - bus Ethernet – magistrala komunikacyjna łącząca urządzenia i procesor,
        - bus HWConnection – magistrala sprzętowa do komunikacji między CPU a RAM,
    - **process**:
        - process UserInterface – interfejs użytkownika wysyłający żądania rezerwacji i odbierający odpowiedzi,
        - process ReservationSystem – system rezerwacji, który sprawdza status książki i generuje odpowiedź,
        - process InventoryManager – menedżer inwentarza obsługujący zapytania o status książek i połączenia z bazą danych,
        - process EventLogger – logger zdarzeń rejestrujący działania w systemie,

    - **thread**:
        - thread UIThread – wątek interfejsu użytkownika przetwarzający dane wejściowe i wyjściowe,
        - thread ReservationThread – wątek logiki rezerwacyjnej obsługujący komunikację z menedżerem inwentarza i loggerem,
        - thread DBThread – wątek obsługujący zapytania do bazy danych i status książek,
        - thread LoggerThread – wątek rejestrujący zdarzenia w systemie.
