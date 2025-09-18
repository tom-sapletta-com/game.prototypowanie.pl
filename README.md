# game.prototypowanie.pl - symulator prototypowania uczy myślenia inżynierskiego poprzez iteracyjne rozwiązywanie problemów projektowych.
  
Gra **uczy myślenia inżynierskiego** poprzez:
- Analizę wzorców
- Identyfikację kluczowych elementów
- Iteracyjne doskonalenie
- Zrozumienie struktury, nie kopiowanie


<img width="2229" height="1147" alt="grafik" src="https://github.com/user-attachments/assets/4f28ffad-1509-4abc-a1be-701fd11f0fa8" />
Edukacyjną gra - symulator prototypowania, który uczy myślenia inżynierskiego poprzez iteracyjne rozwiązywanie problemów projektowych.
System jest wystarczająco "inteligentny", by rozpoznać czy użytkownik zrozumiał zasadę konstrukcji, nawet jeśli rysunek nie jest idealny
Zawiera system wzorów referencyjnych i inteligentny algorytm walidacji, który ocenia strukturalną poprawność, a nie perfekcję rysunku.
System resetuje się i loguje wszystkie zdarzenia IO. Otwórz konsolę (F12) aby zobaczyć szczegółowe logi! 🎮


## SPECYFIKACJA

## 🎮 Kluczowe cechy gry:

### **Mechanika 3-etapowego prototypowania:**
1. **ANALIZA** (niebieski) - zrozumienie problemu
2. **SZKIC** (zielony) - planowanie rozwiązania  
3. **PROTOTYP** (czerwony) - finalne rozwiązanie

### **System progresji:**
- Start: siatka **4x4** (łatwa precyzja)
- Co 2 poziomy: siatka się zagęszcza (8x8, 16x16)
- Od poziomu 3: timer wymusza szybsze decyzje
- Punktacja premiuje ukończenie etapów, nie perfekcję rysunku

### **Wyzwania inżynierskie:**
- **Most** - struktury nośne
- **Dźwignia** - mechanika sił
- **Przekładnia** - przekazywanie ruchu
- **Zbiornik** - projektowanie pojemników
- **Ramię robota** - mechanizmy złożone

### **Narzędzia:**
- ✏️ **Rysowanie** - różne kolory dla każdego etapu
- 📏 **Linia** - do precyzyjnych konstrukcji
- 🧹 **Gumka** - poprawianie błędów

### **Interfejs:**
- Działa natywnie w przeglądarce (HTML5 Canvas)
- Pełna obsługa **mobile** (touch) i **desktop** (mysz)
- Responsywny design
- Intuicyjne podpowiedzi dla każdego etapu

### **Aspekt edukacyjny:**
Gra uczy prawdziwego procesu prototypowania:
- **Dekompozycja problemu** na mniejsze części
- **Iteracyjne doskonalenie** rozwiązania
- **Myślenie przestrzenne** dzięki siatce
- **Zarządzanie czasem** w późniejszych poziomach
- **Analiza → Projekt → Implementacja** jak w prawdziwej inżynierii



## 🎯 Kluczowe ulepszenia:

### **Algorytm walidacji:**
```javascript
// System dzieli canvas na komórki siatki i sprawdza:
- Zajętość każdej komórki (% wypełnienia pikselami)
- Porównanie ze wzorem referencyjnym
- Ważenie stref krytycznych (fundamenty, połączenia)
- Tolerancja niedoskonałości (próg 10% zajętości)
```

### **Wzory referencyjne:**
- **3 wzory** dla każdego wyzwania (progresja złożoności)
- **Wizualizacja** po lewej stronie ekranu
- **Strefy krytyczne** (czerwone) - elementy obowiązkowe
- Możliwość ukrycia/pokazania wzoru

### **System oceniania:**
- **Zielone pola** ✅ - poprawnie narysowane
- **Czerwone pola** ❌ - brakujące elementy  
- **Pomarańczowe pola** ⚠️ - dodatkowe (dozwolone)
- **Dokładność %** - widoczna w czasie rzeczywistym
- **Bonus** za strefy krytyczne (np. filary mostu)

### **Progresja trudności:**
1. **Etap 1 (Analiza)** - podstawowa struktura (60% elementów)
2. **Etap 2 (Szkic)** - więcej detali (80% elementów)
3. **Etap 3 (Prototyp)** - kompletne rozwiązanie (100%)

### **Inteligentna walidacja:**
- Nie wymaga idealnego rysunku
- Sprawdza **logikę konstrukcji**, nie piksele
- Minimum 60% zgodności do przejścia dalej
- Premiuje kluczowe elementy konstrukcyjne

### **Wzory dla 5 wyzwań:**
1. **Most** - filary + pomost + wzmocnienia
2. **Dźwignia** - punkt podparcia + ramiona + siły
3. **Przekładnia** - koła zębate + połączenia
4. **Zbiornik** - ściany + zawór + poziom max
5. **Ramię robota** - podstawa + przeguby + chwytak




### **1. Grubość linii = 50% komórki siatki**
- Linia automatycznie skaluje się: `(canvas.width / gameState.gridDivisions) * 0.5`
- Na siatce 4x4 → gruba linia
- Na siatce 16x16 → cieńsza linia
- Zaokrąglone końce dla lepszego wyglądu

### **2. Timer i Accuracy nad canvasem**
- Przeniesione do sekcji `canvas-info` ponad obszarem rysowania
- Timer po lewej, accuracy po prawej
- Czysta przestrzeń rysowania bez przeszkadzających elementów

### **3. Wzory na całym canvasie**
- Wzory teraz skalują się na **pełny obszar** canvas
- Wzór 4x4 rozciąga się na siatkę 8x8 lub 16x16
- Proporcjonalne powiększenie dla lepszej widoczności

### **4. Toast notifications zamiast popupów**
- **Powiadomienia na dole** ekranu (nie przeszkadzają)
- Różne kolory:
  - 🟢 **Zielony** - sukces (>80% dokładności)
  - 🟡 **Pomarańczowy** - ostrzeżenie (60-80%)
  - 🔴 **Czerwony** - błąd (<60%)
- Znikają automatycznie po 3 sekundach
- Popup tylko przy **ukończeniu poziomu** (to ważny moment)

### **5. Dodatkowe ulepszenia:**
- Lepsza walidacja dla skalowanych wzorów
- Płynniejsze przejścia między etapami
- Czytelniejsze komunikaty bez przerywania gry

Teraz gra jest **znacznie bardziej grywalna**:
- Grube, widoczne linie dostosowane do siatki
- Wzory wykorzystują pełną przestrzeń
- Nic nie przeszkadza podczas rysowania
- Informacje pojawiają się dyskretnie na dole



# CHANGELOG

## ✅ **Główne naprawy:**

### **1. Ekran przejścia ukryty na starcie**
- Dodałem `display: none !important` w CSS
- Ekran pojawi się tylko podczas przejść między poziomami

### **2. Naprawione przejścia między poziomami**
- Poprawiona sekwencja: Feedback (2s) → Transition (1.5s) → New Level
- Pełne resetowanie stanu dla nowego poziomu
- Prawidłowe ładowanie nowych wyzwań
- Stage wraca do 1 dla każdego nowego poziomu

### **3. Logowanie zdarzeń IO**
```javascript
[IO 14:23:45] MOUSE_MOVE: Vector: [125, -67], Magnitude: 142, Angle: -28°
[IO 14:23:45] CLICK: Target: BUTTON#nextStage, Position: [456, 234]
[IO 14:23:45] KEY_DOWN: Key: Space, Code: Space, Ctrl: false, Shift: false
[IO 14:23:45] TOUCH_START: Position: [234, 456], Touches: 1
[IO 14:23:45] DRAW_START: Position: [125, 200], Tool: pen, LineWidth: 43.8
[IO 14:23:45] DRAW_MOVE: Points: 20, Last: [145, 210]
[IO 14:23:45] DRAW_END: Stroke completed with 45 points, Total strokes: 3
```

### **4. Wektorowa reprezentacja ruchu myszy**
- Loguje ruch gdy przemieszczenie > 50px
- Pokazuje wektor [x, y], magnitude i kąt
- Throttling dla touchmove i mousemove

### **5. Naprawione wielokrotne wywoływanie initCanvas**
- Dodałem debounce 250ms dla resize
- Usuwam stare event listenery przed dodaniem nowych
- Brak duplikacji listenerów

### **6. Ulepszone logowanie**
```
[PREPARE NEXT] Starting preparation for level 3
[PREPARE NEXT] Grid size changed from 4 to 8
[UPDATE STAGE] Stage 1 marked as active
[LOAD CHALLENGE] UI updated for level 3
🎮 GO! Start drawing!
```

### **7. Dodatkowe ulepszenia**
- Toast "Poziom X - START!" po przejściu
- Hint pokazuje się na 5s przy nowym poziomie
- Timer nie pokazuje się przed poziomem 4
- Lepsza synchronizacja UI

## **Monitorowanie IO:**
- **Mysz**: pozycja, kliknięcia, wektory ruchu
- **Klawiatura**: wciśnięte klawisze z modyfikatorami
- **Touch**: start, move (throttled), end
- **Focus**: śledzenie focusu na elementach
- **Rysowanie**: start/move/end z liczbą punktów

