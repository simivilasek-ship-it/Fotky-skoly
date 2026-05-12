# TailGallery – responzivní fotogalerie s Lightbox2

Tento návod ukazuje, jak vytvořit responzivní galerii 8 náhodných fotek v Tailwind CSS a otevření obrázků řešit přes klasickou knihovnu Lightbox2.

## Co budete mít na konci

- stránku s galerií 8 fotek,
- responzivní grid (1/2/4 sloupce),
- otevření fotky v Lightbox2,
- přepínání fotek v lightboxu,
- prezentaci (slideshow) přímo v Lightbox2,
- build stylů do `src/output.css`.

---

## 1) Instalace závislostí

V kořeni projektu spusťte:

```bash
npm install
```

---

## 2) Tailwind vstup

Soubor `src/input.css`:

```css
@import "tailwindcss";
```

---

## 3) Vytvořte `index.html` s Lightbox2

Do HTML přidejte:

1. Tailwind CSS výstup (`./src/output.css`)
2. Lightbox2 CSS v `<head>`
3. Galerie obrázků přes `<a data-lightbox="tailgallery">`
4. Na konec stránky jQuery + Lightbox2 JS

Kompletní šablona:

```html
<!doctype html>
<html lang="cs">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Responzivní fotogalerie</title>
    <link rel="stylesheet" href="./src/output.css" />
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/lightbox2/2.11.5/css/lightbox.min.css" />
  </head>
  <body class="bg-slate-100 text-slate-900">
    <main class="mx-auto max-w-7xl px-4 py-10 sm:px-6 lg:px-8">
      <h1 class="mb-2 text-3xl font-bold tracking-tight">Moje fotogalerie</h1>
      <p class="mb-8 text-slate-600">8 náhodných fotografií přes Picsum Photos</p>

      <section class="grid grid-cols-1 gap-4 sm:grid-cols-2 lg:grid-cols-4">
        <figure class="group overflow-hidden rounded-2xl bg-white shadow-sm">
          <a href="https://picsum.photos/seed/1/1600/1200" data-lightbox="tailgallery" data-title="Náhodná fotka 1" class="block w-full cursor-zoom-in">
            <img src="https://picsum.photos/seed/1/800/600" alt="Náhodná fotka 1" class="h-64 w-full object-cover transition duration-300 group-hover:scale-105" loading="lazy" />
          </a>
        </figure>
        <figure class="group overflow-hidden rounded-2xl bg-white shadow-sm">
          <a href="https://picsum.photos/seed/2/1600/1200" data-lightbox="tailgallery" data-title="Náhodná fotka 2" class="block w-full cursor-zoom-in">
            <img src="https://picsum.photos/seed/2/800/600" alt="Náhodná fotka 2" class="h-64 w-full object-cover transition duration-300 group-hover:scale-105" loading="lazy" />
          </a>
        </figure>
        <figure class="group overflow-hidden rounded-2xl bg-white shadow-sm">
          <a href="https://picsum.photos/seed/3/1600/1200" data-lightbox="tailgallery" data-title="Náhodná fotka 3" class="block w-full cursor-zoom-in">
            <img src="https://picsum.photos/seed/3/800/600" alt="Náhodná fotka 3" class="h-64 w-full object-cover transition duration-300 group-hover:scale-105" loading="lazy" />
          </a>
        </figure>
        <figure class="group overflow-hidden rounded-2xl bg-white shadow-sm">
          <a href="https://picsum.photos/seed/4/1600/1200" data-lightbox="tailgallery" data-title="Náhodná fotka 4" class="block w-full cursor-zoom-in">
            <img src="https://picsum.photos/seed/4/800/600" alt="Náhodná fotka 4" class="h-64 w-full object-cover transition duration-300 group-hover:scale-105" loading="lazy" />
          </a>
        </figure>
        <figure class="group overflow-hidden rounded-2xl bg-white shadow-sm">
          <a href="https://picsum.photos/seed/5/1600/1200" data-lightbox="tailgallery" data-title="Náhodná fotka 5" class="block w-full cursor-zoom-in">
            <img src="https://picsum.photos/seed/5/800/600" alt="Náhodná fotka 5" class="h-64 w-full object-cover transition duration-300 group-hover:scale-105" loading="lazy" />
          </a>
        </figure>
        <figure class="group overflow-hidden rounded-2xl bg-white shadow-sm">
          <a href="https://picsum.photos/seed/6/1600/1200" data-lightbox="tailgallery" data-title="Náhodná fotka 6" class="block w-full cursor-zoom-in">
            <img src="https://picsum.photos/seed/6/800/600" alt="Náhodná fotka 6" class="h-64 w-full object-cover transition duration-300 group-hover:scale-105" loading="lazy" />
          </a>
        </figure>
        <figure class="group overflow-hidden rounded-2xl bg-white shadow-sm">
          <a href="https://picsum.photos/seed/7/1600/1200" data-lightbox="tailgallery" data-title="Náhodná fotka 7" class="block w-full cursor-zoom-in">
            <img src="https://picsum.photos/seed/7/800/600" alt="Náhodná fotka 7" class="h-64 w-full object-cover transition duration-300 group-hover:scale-105" loading="lazy" />
          </a>
        </figure>
        <figure class="group overflow-hidden rounded-2xl bg-white shadow-sm">
          <a href="https://picsum.photos/seed/8/1600/1200" data-lightbox="tailgallery" data-title="Náhodná fotka 8" class="block w-full cursor-zoom-in">
            <img src="https://picsum.photos/seed/8/800/600" alt="Náhodná fotka 8" class="h-64 w-full object-cover transition duration-300 group-hover:scale-105" loading="lazy" />
          </a>
        </figure>
      </section>
    </main>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/lightbox2/2.11.5/js/lightbox.min.js"></script>
    <script>
      lightbox.option({
        albumLabel: "Obrázek %1 z %2",
        wrapAround: true,
        disableScrolling: true,
        fadeDuration: 200,
        imageFadeDuration: 200,
        resizeDuration: 200,
      });
    </script>
  </body>
</html>
```

---

## 4) Návod na lightbox prezentaci (Lightbox2)

Lightbox2 má slideshow zabudovanou.

1. Všechny fotky musí mít stejnou skupinu v `data-lightbox`, např. `data-lightbox="tailgallery"`.
2. Otevři libovolnou fotku v lightboxu.
3. V overlay klikni na `Start Slideshow`.
4. Prezentaci zastavíš přes `Stop Slideshow`.

Tipy:

- `wrapAround: true` umožní plynulé přepínání dokola.
- `disableScrolling: true` vypne scroll stránky během otevřeného lightboxu.
- Text čítače upravíš přes `albumLabel`.

---

## 5) Vygenerujte Tailwind CSS

Jednorázový build:

```bash
npx @tailwindcss/cli -i ./src/input.css -o ./src/output.css
```

Watch režim:

```bash
npx @tailwindcss/cli -i ./src/input.css -o ./src/output.css --watch
```

---

## 6) Otevřete stránku

Otevřete `index.html` v prohlížeči (doporučeně přes Live Server).

---

## Nejčastější problémy

1. **Lightbox se neotevře**  
   Zkontrolujte, že se načetl jQuery a `lightbox.min.js` bez chyby v konzoli.

2. **Neaplikují se Tailwind styly**  
   Ověřte odkaz na `./src/output.css` a spusťte build znovu.

3. **Fotky se nenačítají**  
   Obrázky jsou z externí služby `picsum.photos`, je potřeba internet.

---

Hotovo – galerie běží na Tailwind CSS a lightbox je řešený přes klasickou knihovnu Lightbox2.
